# gostream

gostream is a library to simplify the streaming of images as video to a series of WebRTC peers. The impetus for this existing was for doing simple GUI / video streaming to a browser all within go with as little cgo as possible. The package will likely be refactored over time to support some more generalized use cases and as such will be in version 0 for the time being. Many parameters are hard coded and need to be configurable over time. Use at your own risk, and please file issues!

## TODO

- [ ] Address code TODOs (including context.TODO)

## Examples

* Stream current desktop: `go run github.com/edaniels/gostream/cmd/stream_desktop`
* Stream an im-gui: `go run github.com/edaniels/gostream/cmd/stream_imgui --image some image`

## Notes

### Using mDNS

* mDNS (.local addresses) don't seem to work well with WebRTC yet. Random STUN/TURN failures appear to occur. At your own risk, you can address this in Firefox in `about:config` with `media.peerconnection.ice.obfuscate_host_addresses` set to `false` and in Chrome with `chrome://flags/#enable-webrtc-hide-local-ips-with-mdns` set to `Disabled`.

## Building

### Prerequisites

* libvpx

Linux: `libvpx-dev`

macOS: `brew install libvpx`

## Development

### Linting

```
go run github.com/golangci/golangci-lint/cmd/golangci-lint run -v ./...
go get -u github.com/edaniels/golinters/cmd/combined
go vet -vettool=$(which combined) ./...
```

## Acknowledgements

* https://github.com/poi5305/go-yuv2webRTC - for some very helpful utilities and knowledge building

If I somehow took code from somewhere without acknowledging it here or via the go.mod, please file an issue and let me know.
