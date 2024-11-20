# Check JWT Auth Token Validity

```swift

import Foundation

func isJWTExpired(_ token: String) -> Bool {
        // Split the JWT into its components (header, payload, signature)
        let segments = token.split(separator: ".")
        guard segments.count == 3 else {
            return true // If the token doesn't have 3 parts, consider it invalid or expired
        }

        // Decode the payload segment
        let payloadSegment = segments[1]
        guard let payloadData = Data(base64Encoded: String(payloadSegment)
            .replacingOccurrences(of: "-", with: "+")
            .replacingOccurrences(of: "_", with: "/")
            .padding(toLength: ((payloadSegment.count + 3) / 4) * 4, withPad: "=", startingAt: 0)) else {
            return true // If payload decoding fails, consider it expired
        }

        // Convert the data to a dictionary
        guard let json = try? JSONSerialization.jsonObject(with: payloadData, options: []),
              let payload = json as? [String: Any] else {
            return true // If conversion fails, consider it expired
        }

        // Check the "exp" field
        if let exp = payload["exp"] as? Double {
            let expirationDate = Date(timeIntervalSince1970: exp)
            return expirationDate <= Date() // Returns true if the token is expired
        }

        return true // Consider it expired if the "exp" field is missing
    }



```
