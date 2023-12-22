# Fun Weird Nasty C#
C# snippets That Make You Go Hmmm... 

All snippets are linked to their original creators (or the people I found them from). I don't take any credit, just collating fun bits!

## Smallest C#

```csharp
{}
```

[Via nietras](https://nietras.com/2021/10/09/worlds-smallest-csharp-program/)

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

```csharp
using System;
using System.IO;

Console.WriteLine(Path.DirectorySeparatorChar); // prints '\'

var f = (in char x) => { /* can't modify 'x' here */ };
f = (ref char x) => { x = 'A'; }; // but can here!

f(Path.DirectorySeparatorChar);

Console.WriteLine(Path.DirectorySeparatorChar); // prints 'A'
```

[Via Aleksandr Shvedov](https://twitter.com/controlflow/status/1737788743270965538)

[Sharplab](https://sharplab.io/#v2:EYLgtghglgdgNAFxAJwK4wD4AEBMBGAWACgsAGAAizwDoBJAeQG5jiqBOACgAUIEALagBEoyAKYBjBAHtkATwDKogA4RkvGQGE+qgJSNyAegPklyWAgDO5AOQAdayyIA3VeQBm5ALzkOscuO1kcgAPHS8APnIAb0MAKn8IGGsEcjApABMoN1kbYOtyPlExcljjAF9mIg9vDjEPANdQiOiQrxsAQWt9CsNjYFQU8USCotEAQkc3bl4BYTFJGQVlVXVkLV1K1jxOHn4hEQlpOUUVNSP15D1ekzMYSw7rIA)

## New DateTime formula, *Euclidean affine functions*
```csharp
// Exactly the same as Year, Month, Day properties, except computing all of
// year/month/day rather than just one of them. Used when all three
// are needed rather than redoing the computations for each.
//
// Implementation based on article https://arxiv.org/pdf/2102.06959.pdf
//   Cassio Neri, Lorenz Schneiderhttps - Euclidean Affine Functions and Applications to Calendar Algorithms - 2021
internal void GetDate(out int year, out int month, out int day)
{
    // y400 = number of whole 400-year periods since 3/1/0000
    // r1 = day number within 400-year period
    (uint y400, uint r1) = Math.DivRem(((uint)(UTicks / TicksPer6Hours) | 3U) + 1224, DaysPer400Years);
    ulong u2 = (ulong)Math.BigMul(2939745, (int)r1 | 3);
    ushort daySinceMarch1 = (ushort)((uint)u2 / 11758980);
    int n3 = 2141 * daySinceMarch1 + 197913;
    year = (int)(100 * y400 + (uint)(u2 >> 32));
    // compute month and day
    month = (ushort)(n3 >> 16);
    day = (ushort)n3 / 2141 + 1;

    // rollover December 31
    if (daySinceMarch1 >= March1BasedDayOfNewYear)
    {
        ++year;
        month -= 12;
    }
}
```

[30% optimization of DateTime.GetDate()/.Year/.Month/.Day/.DayOfYear by 'Euclidean affine functions' #72712](https://github.com/dotnet/runtime/pull/72712)

## ReadOnly lists aren't always readonly
```csharp
using System;
using System.Collections.Generic;

var list = new List<int>{1, 2, 3, 4};

IReadOnlyList<int> readonlyList = list;

// error CS1061: 'IReadOnlyList<int>' does not contain a definition for 'Add'...
// readonlyList.Add(5);

// Works as expected
((List<int>)readonlyList).Add(5);

// 5
Console.WriteLine(readonlyList.Count);
```

[Via Nick Chapsas](https://www.youtube.com/watch?v=7hBPI0xYezo&t=203s)

[Great explanation on SO](https://stackoverflow.com/a/49115272)

## async async async (async async)

```csharp
async async async(async async) => 
        await async;
```

[Via Jared Parsons](https://twitter.com/jaredpar/status/1613615815231934468)
[Explainer from Jared](https://gist.github.com/jaredpar/6706628bfe0098840ce453c1c71098a9)
[Sharplab](https://sharplab.io/#v2:EYLgtghglgdgNAFxFANnAJiA1AHwAIBMAjALABQeADAAR5EB0ASgKYBmKzAxglAPYz0AomCgIA3OSq0GjAK4weYZvQDCvMAAdUzAE4BlXQDconZgGcJFGnQCsl8gGIYslCgjAO1dFDPuO5SQJaPB0uXh10agBvagBfQOoAdwALXWZouPJqbOoEvQQdWABzaKycvABmaQA2aihNFBNRal4NXQgEcOp8wpgigAp0AE8YCBFOakMIHQBKagBeAD5qZ1dLeLIE4dHxjI3K2iCpnQyAshyvEbGTS52bpZWXFEsL19zz8oAWalDOcPR+ik0t0CsUFo9XHA6gpqENweg2BAXAgZmVslE0a8emCzOCEMkfPRttdOC8crELpjXpi8AAOWjVAA8sAQywAsv05hiPm9jpNwTBmIlOWS3ngAJyTeh0/qCxK0Wmcmai154ADs1EoKo2lJ5Cv1MrpCrmDyp5UldPWZwA9NbqAARXiw3iyagqJLJDrUACSAHIwF5eGDUqEAPwJFQxDZnQi0SUgH0AOV4PFYQzUDWYPH4pT1B2AvF4KB9ZgzGg4CGYkQeBVkzBVBzw3wA4lmWGZkZy9jSqk3qAB5GBlitV/p0IJ/BSwWQdPgwLmZMjRsgAbQAgmYRpw2Vnkrx0AAhWSoBE6foIIZtXisfrAY8oU8zGYAXQSRpiPbj1FbCDXiWglZniayz4jovDyqszzkMusZ3ieujkNyFz5vep5dlGn50LUcEProbqhB0zBdg8coiph3wGAg7adguOrlL2FFZoIAAepgaNmMD9CxbEcdQzC0eRILTAgjIACr5IRbIQJwBKCos/ShKw1DiQgknSbJ6RmKplZSTJsD8Wa2RAqEykSTp6n6dQCbehuW5mcwukaQsIHJGBEFPA2vb0ngtQkR5gl/gBg7DlmVZiYFoi6FCKlqXpcn9IZPxsMpEWAXGUVJUpMXmXFmnaQ5FmCqieoXMZ6SialeHWcmqbpuo5ZZnOiVlaZ+WOZZ1m2TAnD2e1grOdQoHgRCUF5gx1CpQAqjAvisMwwX1SO6Dhf+kU6NFvWFcw8mJYpKWrWlEoZXt2UFbl1BabFGnFW8RkhuVlUnNZKiFDwnAQCgNVQGmIUcc192tVdHU+l1PVtVtA1De5ayCZRm25f0Nmbt18NOZdOXXZDrnDZBVpkEAA==)

## async async async (async async) Part 

```csharp
[async, async<async>] async async async([async<async>, async] (async async, async) async)
        => await async.async;
```

[Via Lucas Trzesniewski](https://twitter.com/Lucas_Trz/status/1613628484315713576)
[Sharplab](https://sharplab.io/#v2:EYLgtghglgdgNAFxFANnAJiA1AHwAIBMAjALABQeADAAR5EB0ASgK4wJRgCm9AwgPZgADqk4AnAMpiAblADGnAM4BucuQDEMZihQRgKTtXRQFu/aooBmWgWpSIo6gG9qL12/Ju8ADloAWagCyABQAlE4ebq54AJzUMJwA7rb2ofTeQeicAGYQWgghKmRuAL4RLmXUFQDa3nC0XgA83gB8ALr1Hek1jS113u1B3vV9XmHeIRVuALzNtLHeaV6F5qVk5uSEc9Qg1ACSAHJ87FkAnvxC+ux8MOFFUVbAfHwoewrngpec6NQz1AiizE4hU8Vjw/gA4pwEIxFHlQk5qKsQX5qAB5GDvT7oQZEGyya7sTQQK4wMLOVarchVACCChOMFkAShAAs+OgAELMVCZURBBAnQScPhZILALkoHkhEKtDY2IbOCp4UGxSEIakJaAIMTw34IZmiPhJTTaQqUsg0hD/KBirUAVRMAHNOEFqZbRNbmFqACr2J0IBT0anaOpBlCGgJ5KAfAxTP4AzjS2X1V1Wm0GHYp91ppxmi2pz2ce0QJ0ut0e72+qEB0Mh7ThyPRn5xwGJihyryZ8ucBpe2YZsvZxxmzZi7liciORUPcU8+Hkqe0IgANmoo4lYmoPFEnGJzrCv3iCVCwPuKMk0NhKAQc8RC7B1HPAFEAB7yQQkoIvt8k6gJhFI0973EBB7AQHtgN3AIIFkZlYE4Zogm3LJqC9CCtSgmC4OoBQQPQ6DYPiCY7kiagEmZMQDFQ3DOAwgj0z2Wl6VkNCaPwrDdX1Q04i0FATxcJVOhXA8eL42hQX8dVNXRTEoS+HtJKgLVRDqKjILY+IEMmVwkJQhSlLmMQ6h01S8Mw+JsOo2i4KIkiXDIijdI1RSNx2A4jigU4ZJJLS7PI7cUJYqzzNcxiGUC9SY1mPUDSNES7wkpyEFtGATCyThpIEaMtXQeTEsMgLLIizTiMiYy9I3GJ8uM8KzIMHC1NqmzbPs/yvXKhxXK3RS5AgFBDmOM5MsuKBrh80i/Momq6O2Bi6TCwrap+KLONik14ofKEprgoJdlC5iFum+rTLo/dlpi7i1rIVYgA===)

## Floats are inaccurate

```csharp
using System;
float x = 0.4f;
float y = 0.6f;
Console.WriteLine((double)x + (double)y == 1);
Console.WriteLine((float)((double)x + (double)y) == 1);
```

[Via Ashley Hauck](https://twitter.com/khyperia/status/1730232117831815322)
[Explainer by Ashley Hauck](https://mas.to/@khyperia/111500086973840518)
[Sharplab](https://sharplab.io/#v2:C4LgTgrgdgPgAgJgIwFgBQAzANgewIbAAEAHoQLyEAMAdACwYDc62+RAnuVdQGyPpxIAnAAphAExwQARlgCmASlIBqQuMkyFHMhSTymaASOEsC80ROlzFhFWsub55HXqA)

