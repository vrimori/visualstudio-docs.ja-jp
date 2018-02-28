---
title: "方法: 編集と中断モードで編集を適用して続行 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 54fb069f5328dd9bc7cabab16c0688109312dfd1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue"></a>方法 : エディット コンティニュの中断モード時に編集を適用する
エディット コンティニュを使用すると、中断モードでコードを編集した後、コードを停止したり再起動したりせずにデバッグを継続できます。  
  
デバッグ中にエディット コンティニュの使用に関する制限については、次を参照してください[サポートされているコードの変更 (c# および Visual Basic](../debugger/supported-code-changes-csharp.md)]。
  
### <a name="to-edit-code-in-break-mode"></a>中断モードでコードを編集するには  
  
1.  以下のいずれかの操作を行って中断モードに入ります。  
  
    -   選択し、コードにブレークポイントを設定**デバッグの開始**から、**デバッグ**メニューとアプリケーション、ブレークポイントにヒットするを待っています。  
  
         - または -  
  
    -   デバッグを開始し、**すべて中断**から、**デバッグ**メニュー。  
  
         - または -  
  
    -   例外が発生するときに選択**編集を有効にする**上、**例外処理アシスタント**です。  
  
2.  必要なサポートされているコード変更を加えます。  
  
     詳細については、次を参照してください。[サポートされているコードの変更 (c# および Visual Basic](../debugger/supported-code-changes-csharp.md)です。  
  
    > [!NOTE]
    >  エディット コンティニュで許可されないコード変更を行おうとすると、編集部分の下に紫の波線が表示され、タスク一覧にタスクが表示されます。 この場合、無効なコード変更を元に戻さない限り、コードの実行を続行できません。  
  
3.  **デバッグ** メニューのをクリックして**続行**実行を再開します。  
  
     適用した編集がプロジェクトに取り込まれた状態でコードが実行されます。  
  
## <a name="see-also"></a>参照  
 [サポートされているコード変更 (c# および Visual Basic](../debugger/supported-code-changes-csharp.md)   
 [エディット コンティニュ (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)