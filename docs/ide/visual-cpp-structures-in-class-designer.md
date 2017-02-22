---
title: "Visual C++ Structures in Class Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Class Designer [Visual Studio], structures"
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Visual C++ Structures in Class Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

クラス デザイナーは、C\+\+ の構造体をサポートしています。これは、`struct` キーワードを使用して宣言されます。  例を次に示します。  
  
```  
struct MyStructure  
{  
   char a;  
   int i;  
   long j;  
};  
```  
  
 `struct` 型の使用法の詳細については、「[struct](/visual-cpp/cpp/struct-cpp)」を参照してください。  
  
 クラス ダイアグラムにおける C\+\+ 構造体の図形の形状と動作はクラスの図形に似ていますが、ラベルが **\[Struct\]** である点と、角が丸くなく直角になっている点が異なります。  
  
|コード要素|\[クラス デザイナー\] ビュー|  
|-----------|-----------------------|  
|`struct StructureName {};`|**StructureName**<br /><br /> 構造体|  
  
## 参照  
 [Working with Visual C\+\+ Code \(Class Designer\)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [クラスと構造体](/visual-cpp/cpp/classes-and-structs-cpp)   
 [struct](/visual-cpp/cpp/struct-cpp)