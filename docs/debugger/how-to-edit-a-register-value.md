---
title: '方法: レジスタ値を編集 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.register.edit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, editing register values
- register values
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: de743aa67b3875654dee1b13b27a74e208bb6d53
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31475004"
---
# <a name="how-to-edit-a-register-value"></a>方法 : レジスタ値を編集する
[レジスタ] ウィンドウがアドレス レベルのデバッグが有効になっている場合にのみ使用できますが、**オプション**ダイアログ ボックスで、**デバッグ**ノード。  
  
### <a name="to-change-the-value-of-a-register"></a>レジスタ値を変更するには  
  
1.  **登録**ウィンドウを使用して、TAB キーまたはカーソルを移動するには、マウスを変更する値をポイントします。 入力するときは、上書きする値の直前の位置にカーソルを置く必要があります。  
  
2.  新しい値を入力します。  
  
    > [!CAUTION]
    >  レジスタ値を変更すると (特に EIP レジスタと EBP レジスタの場合は)、プログラムの実行に影響する場合があります。  
  
    > [!CAUTION]
    >  浮動小数点値を編集すると、小数部分の 10 進とバイナリの変換により、多少の誤差が発生する場合があります。 特に影響のないように見える編集でも、浮動小数点レジスタの最下位バイトが変化する場合があります。  
  
## <a name="see-also"></a>関連項目  
 [方法: [レジスタ] ウィンドウを使用する](../debugger/how-to-use-the-registers-window.md)