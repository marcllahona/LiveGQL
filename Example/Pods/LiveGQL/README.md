![LiveGQL: Use GraphQL Websocket subscription in Swift](http://i.imgur.com/kW0Mtet.png)

LiveGQL is a simple library to use GraphQL Subscribtion on WebSocket based on [Apollo Protocol](https://github.com/apollographql/subscriptions-transport-ws/blob/master/PROTOCOL.md).

*Hello folks! I made this simple prototype of a future complete library, you can try it now and see in your console how does it work! I will provide a fully functionnal version (for data handling and full protocol implemented) next week!*

- [Features](#features)
- [Requirements](#requirements)
- [Communication](#communication)
- [Installation](#installation)
- [Usage](#usage)

## Features

- [x] Connect to a GraphQL WebSocket server
- [x] Send messages
- [x] Subscribe / unsubscribe
- [x] Close connection
- [x] Data handling (delegate)
- [ ] Error handling
- [ ] JSON parsing
- [ ] Implement all Apollo protocol (today just Client part totally implemented)

## Requirements

- iOS 9.0
- Xcode >= 8.1
- Swift >= 3.0

We also use [Starscream](https://github.com/daltoniam/Starscream) and [JSONCodable](https://github.com/matthewcheok/JSONCodable), thank you them

## Communication

- Use issue if you have any problem
- Don't hesitate to contribute to the project with a pull request

## Installation

### CocoaPods

```ruby
source 'https://github.com/CocoaPods/Specs.git'
platform :ios, '10.0'
use_frameworks!

target '<Your Target Name>' do
    pod 'LiveGQL', '~> 0.0.4'
end
```

### Manually

Just copy files in the Source folder!


## Usage

### Initializing

Important: to not fall out the variable in the scope, please instantiate above your viewDidLoad() for example.

```swift
import LiveGQL

let gql = LiveGQL(socket: "ws://localhost:7003/feedback")

gql.initServer()
```

### Subscribe / Unsubscribe

#### Subscribe

Just call subscribe method, set an identifier and your subscription query as well.

```swift
gql.subscribe(graphql: "subscription {feedbackAdded {id, text}}", identifier: "feed")
```

You can't treat properly server message now, it will come in the next version, this is just a first preview of implementation, you can see result in the console.

#### Unsubscribe

Just call unsubscribe method and your identifier

```swift
gql.unsubscribe(subscribtion: "feed")
```

### Close connection

```swift
gql.closeConnection()
```