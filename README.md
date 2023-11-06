# Run

RUSTFLAGS="--cfg async_executor_impl=\"async-std\" --cfg async_channel_impl=\"async-std\"" cargo build --release && docker build -f Dockerfile -t ghcr.io/espressosystems/espresso-sequencer/blocks-stream:main . && docker run --network host -v /home/dymchenko/m:/machines -e CELESTIA_NODE_AUTH_TOKEN_WRITE=$(docker compose -f ci/docker-compose.yml exec bridge celestia bridge auth admin --p2p.network private) -t ghcr.io/espressosystems/espresso-sequencer/blocks-stream:main