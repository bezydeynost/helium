Add flake toinputs:

```nix
inputs.helium = {
  url = "github:bezydeynost/helium-browser-nix-flake";
  inputs.nixpkgs.follows = "nixpkgs";
};
```

Add it to packages:

```nix
environment.systemPackages = [
  inputs.helium.packages.${system}.default
];
```

Overlay

```nix
nixpkgs.overlays = [
  inputs.helium.overlays.default
];
```

Then use it anywhere as `pkgs.helium`:

```nix
environment.systemPackages = with pkgs; [
  helium
];
```
