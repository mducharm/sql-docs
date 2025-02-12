---
description: "AddCalculatedMembers (MDX)"
title: "AddCalculatedMembers (MDX) | Microsoft Docs"
ms.date: 02/17/2022
ms.service: sql
ms.subservice: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
---
# AddCalculatedMembers (MDX)


  Returns a set generated by adding calculated members to a specified set.  
  
## Syntax  
  
```  
  
AddCalculatedMembers(Set_Expression)   
```  
  
## Arguments  
 *Set_Expression*  
 A valid Multidimensional Expressions (MDX) expression that returns a set.  
  
## Remarks  
 By default, MDX excludes calculated members when it resolves set functions. The **AddCalculatedMembers** function examines the set expression specified in *Set_Expression,* and includes calculated members that are siblings of the members contained within the scope of that set expression.  
  
> [!NOTE]  
>  This function can be used only with one-dimensional set expressions.  
  
## Examples  
 The following example demonstrates the use of this function.  
  
```  
-- This query returns the calculated members for the cube  
-- by retrieving all members, and then excluding non-calculated members.  
SELECT   
   AddCalculatedMembers(  
      {[Measures].Members}  
      )-[Measures].Members ON COLUMNS  
FROM [Adventure Works]   
```  
  
 The following example returns the `Measures.[Unit Price]` member, in addition to all the calculated members in the **Measures** dimension, from the **Adventure Works** cube.  
  
```  
SELECT  
   AddCalculatedMembers({Measures.[Unit Price]}) ON COLUMNS  
FROM   
   [Adventure Works]  
```  
  
## See Also  
 [MDX Function Reference &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
