---
title: Annotate Curve Endpoints
description: Demonstrates how to add a NURBS curve to Rhino using Python.
authors: ['Dale Fugier']
author_contacts: ['dale']
apis: ['RhinoPython']
languages: ['Python']
platforms: ['Windows', 'Mac']
categories: ['Adding Objects']
origin:
order: 11
keywords: ['script', 'Rhino', 'python']
layout: code-sample-python
---

```python
# Annotate the endpoints of curve objects
import rhinoscriptsyntax as rs

def AnnotateCurveEndPoints():
    """Annotates the endpoints of curve objects. If the curve is closed
    then only the starting point is annotated.
    """
    # get the curve object
    objectId = rs.GetObject("Select curve", rs.filter.curve)
    if objectId is None: return

    # Add the first annotation
    point = rs.CurveStartPoint(objectId)
    rs.AddPoint(point)
    rs.AddTextDot(point, point)

    # Add the second annotation
    if not rs.IsCurveClosed(objectId):
        point = rs.CurveEndPoint(objectId)
        rs.AddPoint(point)
        rs.AddTextDot(point, point)


# Check to see if this file is being executed as the "main" python
# script instead of being used as a module by some other python script
# This allows us to use the module which ever way we want.
if __name__ == "__main__":
    AnnotateCurveEndPoints() # Call the function defined above
```
