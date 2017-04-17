---
title: "クラス デザイナーの Visual C++ 構造体 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 11
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 5f15cb38d9bd9f5035f9c02ef1beaf5d19da143b
ms.lasthandoff: 04/05/2017

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
