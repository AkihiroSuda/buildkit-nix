# Example: nginx (Flake)

## Usage

```bash
export DOCKER_BUILDKIT=1
docker build -t nginx-nix -f flake.nix .
```

```
docker run -d -p 8080:80 --read-only --name nginx-nix nginx-nix
```

## Advanced guides
### Updating dependencies

```bash
nix flake update --override-input nixpkgs github:NixOS/nixpkgs/master
```

You might have to create `~/.config/nix/nix.conf` with the following content:
```
experimental-features = nix-command flakes
```

### Build with `nix build`

```bash
nix build
docker load < result
```
