---
title: ダイアログ ボックスの値を変更することはできません |Microsoft Docs
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
- vs.debug.variables.failededit
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Cannot Change Value dialog box
- variables [debugger], editing
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cde574c1148af649fe421313cb943e1cebb1e221
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49254723"
---
# <a name="cannot-change-value-dialog-box"></a>[値を変更できません] ダイアログ ボックス
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Error  
 `The value of this variable cannot be changed` &#124;`The name` *名前* `does not exist in the current context` &#124; *さまざまな他のメッセージ*  
  
 このメッセージ ボックスが表示されるのは、デバッガー ウィンドウ ([自動変数]、[ウォッチ]、または [ローカル] の各ウィンドウ)、または [クイック ウォッチ] ダイアログ ボックスで変数の内容を不正な値に変更しようとした場合です。 たとえば、整数値を文字列に設定しようとすると、このメッセージ ボックスが表示されます。  
  
## <a name="solution"></a>ソリューション  
 デバッグ用ウィンドウや [クイック ウォッチ] ダイアログ ボックスに入力した内容が、設定する変数に対して有効な値を表していることを確認します。  
  
## <a name="see-also"></a>関連項目  
 [デバッガー内の式](../debugger/expressions-in-the-debugger.md)



