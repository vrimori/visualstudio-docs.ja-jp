---
title: '方法: エディット中断モードで編集を適用して続行 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 263e4bf4505995a4c8eccbe7c33f59115412dda5
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219511"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue"></a>方法 : エディット コンティニュの中断モード時に編集を適用する
エディット コンティニュを使用すると、中断モードでコードを編集した後、コードを停止したり再起動したりせずにデバッグを継続できます。  
  
デバッグ中にエディット コンティニュの使用に関する制限については、次を参照してください[サポートされているコードの変更 (C#および Visual Basic](../debugger/supported-code-changes-csharp.md)]。
  
### <a name="to-edit-code-in-break-mode"></a>中断モードでコードを編集するには  
  
1.  以下のいずれかの操作を行って中断モードに入ります。  
  
    -   コードでブレークポイントを設定し、選択**デバッグの開始**から、**デバッグ**メニューとアプリケーション、ブレークポイントにヒットするまで待ちます。  
  
         - または -  
  
    -   デバッグを開始し、**すべて中断**から、**デバッグ**メニュー。  
  
         - または -  
  
    -   例外が発生したときに選択**編集を有効にする**上、**例外処理アシスタント**します。  
  
2.  必要なサポートされているコード変更を加えます。  
  
     詳細については、次を参照してください。[サポートされているコードの変更 (c# および Visual Basic](../debugger/supported-code-changes-csharp.md)します。  
  
    > [!NOTE]
    >  エディット コンティニュで許可されないコード変更を行おうとすると、編集部分の下に紫の波線が表示され、タスク一覧にタスクが表示されます。 この場合、無効なコード変更を元に戻さない限り、コードの実行を続行できません。  
  
3.  **デバッグ** メニューのをクリックして**続行**実行を再開します。  
  
     適用した編集がプロジェクトに取り込まれた状態でコードが実行されます。  
  
## <a name="see-also"></a>関連項目  
 [サポートされているコード変更 (c# および Visual Basic](../debugger/supported-code-changes-csharp.md)   
 [エディット コンティニュ (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)