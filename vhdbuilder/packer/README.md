The workflow becomes complicated as we add more VHDs. Here is a quick description of the current VHD build workflow:

# gen1
MarketplaceImage->(func/packer) -> VHD in classic SA
## gen1 mariner:
external-vhd->(func/init:internal-vhd)->(func/packer) -> VHD in classic SA

# sig:
MarketplaceImage->(func/init: ensure dest gallery/definition)->(func/packer: managed image)->dest SIG

# gen2:
MarketplaceImage->(func/init: ensure dest existing/static gallery/definition)->(func/packer: managed image)->dest SIG->(func/convert: sig->disk) -> VHD in classic SA

## gen2 mariner:
external-vhd-src->(func/init: ensure dest existing/static gallery/definition, internal-vhd->image; )->source SIG->(func/packer: managed image)->dest SIG->(func/convert: sig->disk) -> VHD in classic SA

# Roadmap
Goal1: remove mariner workflow so things will be simplified.