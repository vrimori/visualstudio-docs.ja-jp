---
title: "クラス デザイナーの Visual C++ 構造体 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 85e2068e00f2164b44feb9aae61a47de426be735
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="visual-c-structures-in-class-designer"></a>クラス デザイナーの Visual C++ 構造体
クラス デザイナーは、C++ の構造体をサポートしています。これは、`struct` キーワードを使用して宣言されます。 例を次に示します。  
  
```  
struct MyStructure  
{  
   char a;  
   int i;  
   long j;  
};  
```  
  
 `struct` 型の使用法の詳細については、「[struct](/cpp/cpp/struct-cpp)」を参照してください。  
  
 クラス ダイアグラムにおける C++ 構造体の図形の形状と動作はクラスの図形に似ていますが、ラベルが **[Struct]** である点と、角が丸くなく直角である点が異なります。  
  
|コード要素|クラス デザイナー ビュー|  
|------------------|-------------------------|  
|`struct StructureName {};`|**StructureName**<br /><br /> 構造体|  
  
## <a name="see-also"></a>関連項目  
 [Visual C++ コードの使用 (クラス デザイナー)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [クラスと構造体](/cpp/cpp/classes-and-structs-cpp)   
 [struct](/cpp/cpp/struct-cpp)