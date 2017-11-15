---
title: "クラス デザイナーの Visual C++ 列挙体 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5cbe3616fa81218c7fbfba31f55d241c3e45dacc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="visual-c-enumerations-in-class-designer"></a>クラス デザイナーの Visual C++ 列挙体
クラス デザイナーでは、C++ の `enum`、およびスコープを持つ `enum class` 型はサポートされていません。 例を次に示します。  
  
```  
enum CardSuit {  
   Diamonds = 1,  
   Hearts = 2,  
   Clubs = 3,  
   Spades = 4  
};  
  
// or...  
enum class CardSuit {  
   Diamonds = 1,  
   Hearts = 2,  
   Clubs = 3,  
   Spades = 4  
};  
  
```  
  
 クラス ダイアグラムにおける C++ 列挙体の図形の形状と動作は構造体の図形に似ていますが、ラベルが **[Enum]** または **[Enum class]** である点と、青ではなくピンクである点、および左と上の余白に色つきの枠がある点が異なります。 列挙体の図形も構造体の図形も、角が直角になっています。  
  
 `enum` 型の使用法の詳細については、「[列挙型](/cpp/cpp/enumerations-cpp)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [Visual C++ コードの使用 (クラス デザイナー)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [列挙型](/cpp/cpp/enumerations-cpp)