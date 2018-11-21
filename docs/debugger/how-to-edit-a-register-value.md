---
title: '方法: レジスタ値を編集 |Microsoft Docs'
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
ms.openlocfilehash: 0d0337f7c77d1ed601c7a6c13c702f4758cbfdbd
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257082"
---
# <a name="how-to-edit-a-register-value-c-c-visual-basic-f"></a>方法: レジスタ値を編集 (C#、C++、Visual Basic、 F#)

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