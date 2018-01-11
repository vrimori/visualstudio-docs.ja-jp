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
ms.workload: cplusplus
ms.openlocfilehash: d6f2aa3893a230abd52dd5cf19ed9d751e56e50c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="visual-c-structures-in-class-designer"></a>クラス デザイナーの Visual C++ 構造体
クラス デザイナーは、C++ の構造体をサポートしています。これは、`struct` キーワードを使用して宣言されます。 例を次に示します。  
  
```cpp
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
[Visual C++ コードの使用](working-with-visual-cpp-code.md)   
[クラスと構造体](/cpp/cpp/classes-and-structs-cpp)   
[struct](/cpp/cpp/struct-cpp)