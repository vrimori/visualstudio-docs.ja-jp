---
title: '方法: レジスタ値を編集 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.register.edit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Registers window, editing register values
- register values
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 465ecd4e8003b82a0a7dfbab33004ef2b80d7f32
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540035"
---
# <a name="how-to-edit-a-register-value"></a>方法 : レジスタ値を編集する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: レジスタ値を編集](https://docs.microsoft.com/visualstudio/debugger/how-to-edit-a-register-value)します。  
  
[レジスタ] ウィンドウにアドレス レベルのデバッグが有効な場合にのみ使用できますが、**オプション**ダイアログ ボックスで、**デバッグ**ノード。  
  
### <a name="to-change-the-value-of-a-register"></a>レジスタ値を変更するには  
  
1.  **登録**ウィンドウで、TAB キーまたはマウス カーソルを移動するポイント値を変更して使用します。 入力するときは、上書きする値の直前の位置にカーソルを置く必要があります。  
  
2.  新しい値を入力します。  
  
    > [!CAUTION]
    >  レジスタ値を変更すると (特に EIP レジスタと EBP レジスタの場合は)、プログラムの実行に影響する場合があります。  
  
    > [!CAUTION]
    >  浮動小数点値を編集すると、小数部分の 10 進とバイナリの変換により、多少の誤差が発生する場合があります。 特に影響のないように見える編集でも、浮動小数点レジスタの最下位バイトが変化する場合があります。  
  
## <a name="see-also"></a>関連項目  
 [方法: [レジスタ] ウィンドウを使用する](../debugger/how-to-use-the-registers-window.md)





