---
title: クラス デザイナーの Visual C++ 構造体 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 19ffa241fdc1f58500c7065e2cee2a33340e33f8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54794471"
---
# <a name="visual-c-structures-in-class-designer"></a>クラス デザイナーの Visual C++ 構造体
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

クラス デザイナーは、C++ の構造体をサポートしています。これは、`struct` キーワードを使用して宣言されます。 例を次に示します。  
  
```  
struct MyStructure  
{  
   char a;  
   int i;  
   long j;  
};  
```  
  
 `struct` 型の使用法の詳細については、「[struct](http://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6)」を参照してください。  
  
 クラス ダイアグラムにおける C++ 構造体の図形の形状と動作はクラスの図形に似ていますが、ラベルが **[Struct]** である点と、角が丸くなく直角である点が異なります。  
  
|コード要素|クラス デザイナー ビュー|  
|------------------|-------------------------|  
|`struct StructureName {};`|**StructureName**<br /><br /> 構造体|  
  
## <a name="see-also"></a>「  
 [Visual C++ コードの使用 (クラス デザイナー)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [クラスと構造体](http://msdn.microsoft.com/library/516dd496-13fb-4f17-845a-e9ca45437873)   
 [struct](http://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6)
