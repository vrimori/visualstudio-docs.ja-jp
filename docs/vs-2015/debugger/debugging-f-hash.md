---
title: F# のデバッグ |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a5790b81eedb1a1bb9dc65b7ce053089c3bc1470
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533371"
---
# <a name="debugging-f"></a>F# のデバッグ #
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[f# をデバッグ](https://docs.microsoft.com/visualstudio/debugger/debugging-f-hash)します。  
  
F# のデバッグは、他のマネージド言語のデバッグとほとんど同じですが、次の例外があります。  
  
-   **[自動変数]** ウィンドウに f# 変数が表示されません。  
  
-   F# ではエディット コンティニュはサポートされません。 デバッグ セッション中に F# コードを編集することは可能ですが、そのような操作は避けてください。 コードの変更はデバッグ セッション中は適用されないため、デバッグ中に F# コードを編集すると、ソース コードとデバッグ中のコードが一致しなくなります。  
  
-   デバッガーは F# 式を認識しません。 F# のデバッグ中にデバッガー ウィンドウまたはダイアログ ボックスに式を入力するには、式を C# の構文に変換する必要があります。 F# の式を C# に変換するときは、C# では等価を示す比較演算子として == を使用しますが、F# では単一の = を使用することに注意してください。  
  
## <a name="see-also"></a>関連項目  
 [マネージド コードをデバッグする](../debugger/debugging-managed-code.md)



