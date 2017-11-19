---
title: "F# のデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51eaed204db7b50e75a18dfac104a00546770abc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-f"></a>F# のデバッグ
F# のデバッグは、他のマネージ言語のデバッグとほとんど同じですが、次の例外があります。  
  
-   **[自動変数]**ウィンドウに f# 変数は表示されません。  
  
-   F# ではエディット コンティニュはサポートされません。 デバッグ セッション中に F# コードを編集することは可能ですが、そのような操作は避けてください。 コードの変更はデバッグ セッション中は適用されないため、デバッグ中に F# コードを編集すると、ソース コードとデバッグ中のコードが一致しなくなります。  
  
-   デバッガーは F# 式を認識しません。 F# のデバッグ中にデバッガー ウィンドウまたはダイアログ ボックスに式を入力するには、式を C# の構文に変換する必要があります。 F# の式を C# に変換するときは、C# では等価を示す比較演算子として == を使用しますが、F# では単一の = を使用することに注意してください。  
  
## <a name="see-also"></a>関連項目  
 [マネージ コードをデバッグする](../debugger/debugging-managed-code.md)
