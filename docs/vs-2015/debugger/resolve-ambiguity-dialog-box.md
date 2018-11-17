---
title: ダイアログ ボックスのあいまいさの解決 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.Disambig
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Resolve Ambiguity dialog box
- debugger, Resolve Ambiguity dialog box
- debugging [C++], resolving ambiguity
ms.assetid: d9f47455-a116-4c84-8bad-2dfbf4d77f74
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 13458279d1970bd1b398a0de6e74b34b0b3a99a0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807589"
---
# <a name="resolve-ambiguity-dialog-box"></a>[あいまいさの解決] ダイアログ ボックス
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[`Resolve Ambiguity`] ダイアログ ボックスが表示されるのは、表示する場所をデバッガーが選択できない場合です。 たとえば、C++ テンプレートを使用する場合は、単一の関数テンプレートから複数の関数を作成できます。 デバッガーがテンプレートのソースの場所で停止して、`Go To Disassembly` が選択されている場合、デバッガーには複数のオプションがあります。 テンプレートから作成された各関数は独自の逆アセンブリ コードを持っており、デバッガーはどのコードを表示するのかを認識していません。 [`Resolve Ambiguity`] ダイアログ ボックスでは、対応するすべての場所の一覧から目的の場所を選択できます。  
  
 `Choose the specific location`  
 コマンドに対応するすべての場所の一覧を表示します。  
  
 `Address`  
 各関数のメモリ アドレスを表示します。  
  
 `Function`  
 各関数の名前を表示します。  
  
 `Module`  
 関数のオブジェクト コードを含むモジュール (EXE または DLL) を表示します。  
  
## <a name="see-also"></a>関連項目  
 [デバッガー内の式](../debugger/expressions-in-the-debugger.md)



