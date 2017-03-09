---
title: "Attribute コンストラクターに、型 &#39;&lt;type&gt;&#39; のパラメーターが指定されていますが、Integral、Floating-point、または Enum 型のいずれでもないか、あるいは Char、String、Boolean、System.Type またはこれらの型の 1 次元配列です。 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30045"
  - "vbc30045"
helpviewer_keywords: 
  - "BC30045"
ms.assetid: 16899755-7901-4c56-ae90-54c3532e8319
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Attribute コンストラクターに、型 &#39;&lt;type&gt;&#39; のパラメーターが指定されていますが、Integral、Floating-point、または Enum 型のいずれでもないか、あるいは Char、String、Boolean、System.Type またはこれらの型の 1 次元配列です。
カスタム属性の定義に、正しくないデータ型をパラメーターに指定するコンストラクターが含まれています。 属性は、アセンブリのメタデータにシリアル化できるデータ型のみをパラメーターとして取ることができます。  
  
 **エラー ID:** BC30045  
  
### このエラーを解決するには  
  
1.  パラメーターのデータ型を、`Byte`、`Short`、`Integer`、`Long`、`Single`、`Double`、`Char`、`String`、`Boolean`、`System.Type`、または列挙型に変更してください。  
  
## 参照  
 [ビルド内にありません: Visual Basic におけるカスタム属性](http://msdn.microsoft.com/ja-jp/d72d8a5c-8f64-4614-b15b-cad66845d047)