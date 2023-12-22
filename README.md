# Fun Weird Nasty C#
C# snippets That Make You Go Hmmm...

## Smallest C#

```csharp
{}
```
## It's all Greek

```csharp
using System;
unsafe class Program
{
    delegate void bar(int* i);
    static Index ƛ(bar β) => default;
    static void Main(string[] args)
    {
        int[] ω = { };
        int Ʃ = 42;
        int? Φ = 10;
        var ϼ = ω;
        
        ϼ=ω[ƛ(β:Δ=>Φ??=ω[^++Ʃ]/Ʃ|*&Δ[-0%Ʃ]>>1^Φ??0!&~(δ:Ʃ,^Φ..).δ)..(1_0>.0?Ʃ:0b1)];
    }
}
```
[Via Llewellyn Pritchard](https://twitter.com/leppie/status/1492256050774487047)
[Sharplab example](https://sharplab.io/#v2:D4AQTAjAsAUArgOwM4EMBmBTABOHEDssA3rFmVgCYYA2GA5igC7YgAsWARigE4AUAlgkYAqLPwCUAblLkQEAGxYAkgioAPLIGzAXl25ZATcDisAXgB8lDGhRxqjaTHJ5FbLAFkUg3nIAMAbQC6WDx0SOIyZCQOjuSCjAFYgJPAJlhEWAC+9tExQliAlYDJrGCZWWJCAPxYgGXAyRDexVkAbjxYgD/AyQn10eHRLcYJvtr6AFyAKcBmlWVlfb4AegDUc7n+APS5wMIAZCO+ALTeAKRLpqYQMxNl3gCEGwB+vIAtwEO5ADRnAHRv4m/3X2+8EAB9bymN7eMq5IbeDgQcT+TppWBpIA)

## Mutate ReadOnly fields

[Via Aleksandr Shvedov](https://twitter.com/controlflow/status/1737788743270965538)

## New DateTime formula, *Euclidean affine functions*

[30% optimization of DateTime.GetDate()/.Year/.Month/.Day/.DayOfYear by 'Euclidean affine functions' #72712](https://github.com/dotnet/runtime/pull/72712)

## ReadOnly lists aren't readonly

[Via Nick Chapsas](https://www.youtube.com/watch?v=7hBPI0xYezo&t=203s)

## async async async (async async)

[Via Jared Parsons](https://twitter.com/jaredpar/status/1613615815231934468)
[Explainer from Jared](https://gist.github.com/jaredpar/6706628bfe0098840ce453c1c71098a9)
[Sharplab](https://sharplab.io/#v2:EYLgtghglgdgNAFxFANnAJiA1AHwAIBMAjALABQeADAAR5EB0ASgKYBmKzAxglAPYz0AomCgIA3OSq0GjAK4weYZvQDCvMAAdUzAE4BlXQDconZgGcJFGnQCsl8gGIYslCgjAO1dFDPuO5SQJaPB0uXh10agBvagBfQOoAdwALXWZouPJqbOoEvQQdWABzaKycvABmaQA2aihNFBNRal4NXQgEcOp8wpgigAp0AE8YCBFOakMIHQBKagBeAD5qZ1dLeLIE4dHxjI3K2iCpnQyAshyvEbGTS52bpZWXFEsL19zz8oAWalDOcPR+ik0t0CsUFo9XHA6gpqENweg2BAXAgZmVslE0a8emCzOCEMkfPRttdOC8crELpjXpi8AAOWjVAA8sAQywAsv05hiPm9jpNwTBmIlOWS3ngAJyTeh0/qCxK0Wmcmai154ADs1EoKo2lJ5Cv1MrpCrmDyp5UldPWZwA9NbqAARXiw3iyagqJLJDrUACSAHIwF5eGDUqEAPwJFQxDZnQi0SUgH0AOV4PFYQzUDWYPH4pT1B2AvF4KB9ZgzGg4CGYkQeBVkzBVBzw3wA4lmWGZkZy9jSqk3qAB5GBlitV/p0IJ/BSwWQdPgwLmZMjRsgAbQAgmYRpw2Vnkrx0AAhWSoBE6foIIZtXisfrAY8oU8zGYAXQSRpiPbj1FbCDXiWglZniayz4jovDyqszzkMusZ3ieujkNyFz5vep5dlGn50LUcEProbqhB0zBdg8coiph3wGAg7adguOrlL2FFZoIAAepgaNmMD9CxbEcdQzC0eRILTAgjIACr5IRbIQJwBKCos/ShKw1DiQgknSbJ6RmKplZSTJsD8Wa2RAqEykSTp6n6dQCbehuW5mcwukaQsIHJGBEFPA2vb0ngtQkR5gl/gBg7DlmVZiYFoi6FCKlqXpcn9IZPxsMpEWAXGUVJUpMXmXFmnaQ5FmCqieoXMZ6SialeHWcmqbpuo5ZZnOiVlaZ+WOZZ1m2TAnD2e1grOdQoHgRCUF5gx1CpQAqjAvisMwwX1SO6Dhf+kU6NFvWFcw8mJYpKWrWlEoZXt2UFbl1BabFGnFW8RkhuVlUnNZKiFDwnAQCgNVQGmIUcc192tVdHU+l1PVtVtA1De5ayCZRm25f0Nmbt18NOZdOXXZDrnDZBVpkEAA==)

## async async async (async async) Part 2

[Via Lucas Trzesniewski](https://twitter.com/Lucas_Trz/status/1613628484315713576)
[Sharplab](https://sharplab.io/#v2:EYLgtghglgdgNAFxFANnAJiA1AHwAIBMAjALABQeADAAR5EB0ASgK4wJRgCm9AwgPZgADqk4AnAMpiAblADGnAM4BucuQDEMZihQRgKTtXRQFu/aooBmWgWpSIo6gG9qL12/Ju8ADloAWagCyABQAlE4ebq54AJzUMJwA7rb2ofTeQeicAGYQWgghKmRuAL4RLmXUFQDa3nC0XgA83gB8ALr1Hek1jS113u1B3vV9XmHeIRVuALzNtLHeaV6F5qVk5uSEc9Qg1ACSAHJ87FkAnvxC+ux8MOFFUVbAfHwoewrngpec6NQz1AiizE4hU8Vjw/gA4pwEIxFHlQk5qKsQX5qAB5GDvT7oQZEGyya7sTQQK4wMLOVarchVACCChOMFkAShAAs+OgAELMVCZURBBAnQScPhZILALkoHkhEKtDY2IbOCp4UGxSEIakJaAIMTw34IZmiPhJTTaQqUsg0hD/KBirUAVRMAHNOEFqZbRNbmFqACr2J0IBT0anaOpBlCGgJ5KAfAxTP4AzjS2X1V1Wm0GHYp91ppxmi2pz2ce0QJ0ut0e72+qEB0Mh7ThyPRn5xwGJihyryZ8ucBpe2YZsvZxxmzZi7liciORUPcU8+Hkqe0IgANmoo4lYmoPFEnGJzrCv3iCVCwPuKMk0NhKAQc8RC7B1HPAFEAB7yQQkoIvt8k6gJhFI0973EBB7AQHtgN3AIIFkZlYE4Zogm3LJqC9CCtSgmC4OoBQQPQ6DYPiCY7kiagEmZMQDFQ3DOAwgj0z2Wl6VkNCaPwrDdX1Q04i0FATxcJVOhXA8eL42hQX8dVNXRTEoS+HtJKgLVRDqKjILY+IEMmVwkJQhSlLmMQ6h01S8Mw+JsOo2i4KIkiXDIijdI1RSNx2A4jigU4ZJJLS7PI7cUJYqzzNcxiGUC9SY1mPUDSNES7wkpyEFtGATCyThpIEaMtXQeTEsMgLLIizTiMiYy9I3GJ8uM8KzIMHC1NqmzbPs/yvXKhxXK3RS5AgFBDmOM5MsuKBrh80i/Momq6O2Bi6TCwrap+KLONik14ofKEprgoJdlC5iFum+rTLo/dlpi7i1rIVYgA===)

## Floats are inaccurate

[Via Ashley Hauck](https://twitter.com/khyperia/status/1730232117831815322)
[Sharplab](https://sharplab.io/#v2:C4LghgzgtgPgAgJgIwFgBQcDMACR2DC2A3utmbjgGYA2A9mMNgLIAUN9jYANNuw9gCMefRgGMAlMVLkZcAOzYw2AFSDsAamyiA3NLIBfPdiNZedfgHE25zsJuC7HLZJJoZshUwYALAGIA6XwBXCABTABMmIOpgAEsAB2oATwBBcPCWbgdnXTdyQzR9IA)

