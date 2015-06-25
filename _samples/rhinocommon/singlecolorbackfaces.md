---
layout: code-sample
title: singlecolorbackfaces
author: 
categories: ['Other'] 
platforms: ['Cross-Platform']
apis: ['RhinoCommon']
languages: ['C#', 'Python', 'VB.NET']
keywords: ['singlecolorbackfaces']
order: 153
description:  
---



```cs
public class SingleColorBackfacesCommand : Command
{
  public override string EnglishName { get { return "csSingleColorBackfaces"; } }

  protected override Result RunCommand(RhinoDoc doc, RunMode mode)
  {
    var display_mode_descs = //DisplayModeDescription.GetDisplayModes();
      from dm in DisplayModeDescription.GetDisplayModes()
      where dm.EnglishName == "Shaded"
      select dm;

    foreach (var dmd in display_mode_descs)
    {
      RhinoApp.WriteLine("CurveColor {0}", dmd.DisplayAttributes.CurveColor.ToKnownColor());
      RhinoApp.WriteLine("ObjectColor {0}", dmd.DisplayAttributes.ObjectColor.ToKnownColor());
    }
    return Result.Success;
  }
}
```
{: #cs .tab-pane .fade .in .active}

