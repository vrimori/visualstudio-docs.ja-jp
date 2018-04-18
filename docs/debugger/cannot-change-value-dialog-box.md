---
title: ダイアログ ボックスの値を変更することはできません |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Cannot Change Value dialog box
- variables [debugger], editing
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 40bcc1eb26ded43f092d89e62cd6f74b2f4dda73
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="cannot-change-value-dialog-box"></a>[値を変更できません] ダイアログ ボックス
## <a name="error"></a>Error  
 `The value of this variable cannot be changed` &#124;`The name` *名前* `does not exist in the current context` &#124; *さまざまな他のメッセージ*  
  
 このメッセージ ボックスが表示されるのは、デバッガー ウィンドウ ([自動変数]、[ウォッチ]、または [ローカル] の各ウィンドウ)、または [クイック ウォッチ] ダイアログ ボックスで変数の内容を不正な値に変更しようとした場合です。 たとえば、整数値を文字列に設定しようとすると、このメッセージ ボックスが表示されます。  
  
## <a name="solution"></a>ソリューション  
 デバッグ用ウィンドウや [クイック ウォッチ] ダイアログ ボックスに入力した内容が、設定する変数に対して有効な値を表していることを確認します。  
  
## <a name="see-also"></a>関連項目  
 [デバッガー内の式](../debugger/expressions-in-the-debugger.md)