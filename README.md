# DCTLs
My DCTLs for DaVinci Resolve. [Support me here](https://buymeacoffee.com/lucaungaro) if you wish.

## Installation
For the DCTLs to appear in the color page, copy them in the dedicated folder:

- MacOS: `/Library/Application Support/Blackmagic Design/DaVinci Resolve/LUT/DCTL`

- Windows: `C:\ProgramData\Blackmagic Design\DaVinci Resolve\Support\LUT\DCTL`

## Description of included DCTLs
### LU_Tetra.dctl
This is my version of Tetrahedral interpolation. It features all eight corners of the color cube, and allows to weight each vertice with the three primaries. The math is derived from [this whitepaper](https://www.filmlight.ltd.uk/pdf/whitepapers/FL-TL-TN-0057-SoftwareLib.pdf) by Filmlight.

### LU_Wrap_SDR.dctl
Inspired by Steve Yedlin's point of view about HDR, that any display capable of reproducing higher contrast and saturation may also be able to reproduce lower values if intended. This DCTL is expected to be put **after** a display transform to a SDR space. It will convert the code values from this SDR space to Rec.2100 HLG or PQ in a *perceptually uniform* way. That is to say: it wraps the SDR experience in an HDR color space. The math is home-made, with a great deal of help from [Bruce Lindbloom's website](http://www.brucelindbloom.com).
#### Usage
[ Your grade... ] -> [ SDR display transform ] -> [ LU_Wrap_SDR dctl ]
#### Parameters
- `Scene white`: Set the desired output value **in nits** at which the SDR rgb (1, 1, 1) white should be rendered in HDR.
- `HLG display peak`: Set the target display peak for an HLG render **in nits**. This setting is used only if `HDR Output` is set to HLG. If you want to target several different peak luminances, you will need to perform one render for each desired display peak luminance.
- `Input color space`: Set the color space that your SDR display transform is outputting to, and that the DCTL will perceptually match in HDR.
- `Ìnput Transf. function`: Same as above but for the transfer function.
- `HDR Output`: Set the color space and transfer function for your SDR image will be wrapped in. Please note that in order to view the HDR output correctly, you need to have a capable display, and DaVinci Resolve's `Output Color Space` should be tagged accordingly.
