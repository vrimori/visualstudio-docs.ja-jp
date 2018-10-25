---
title: '方法: エディット中断モードで編集を適用して続行 |Microsoft Docs'
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
- VB
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ebab549e6d32b355355e4970f4191ea9a024e871
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49266386"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue"></a>方法 : エディット コンティニュの中断モード時に編集を適用する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

エディット コンティニュを使用すると、中断モードでコードを編集した後、コードを停止したり再起動したりせずにデバッグを継続できます。  
  
 次のデバッグ シナリオでは、エディット コンティニュを使用できません。  
  
-   混合モードでの (ネイティブ/マネージ) デバッグ  
  
-   SQL デバッグ  
  
-   ワトソン博士のダンプのデバッグ  
  
-   未処理の例外を受け取った後のコード編集 ( **[ハンドルされていない例外で呼び出し履歴をアンワインドする]** オプションがオンでない場合)  
  
-   埋め込まれたランタイム アプリケーションのデバッグ  
  
-   デバッグ**にアタッチ**を使用してアプリケーションを実行しているのではなく**開始**から、**デバッグ**メニュー。  
  
-   最適化されたコードのデバッグ  
  
-   マネージ コードのデバッグ (デバッグ対象が 64 ビット アプリケーションである場合)。 エディット コンティニュを使用する場合は、デバッグ対象を x86 に設定する必要があります  (_プロジェクト_**プロパティ**、**コンパイル** タブで、**高度なコンパイラ**設定します。)。  
  
-   ビルド エラーによって新しいバージョンのビルドが失敗した後の旧バージョンのデバッグ  
  
### <a name="to-edit-code-in-break-mode"></a>中断モードでコードを編集するには  
  
1.  以下のいずれかの操作を行って中断モードに入ります。  
  
    -   コードでブレークポイントを設定し、選択**デバッグの開始**から、**デバッグ**メニューとアプリケーション、ブレークポイントにヒットするまで待ちます。  
  
         または  
  
    -   デバッグを開始し、**すべて中断**から、**デバッグ**メニュー。  
  
         または  
  
    -   例外が発生したときに選択**編集を有効にする**上、**例外処理アシスタント**します。  
  
2.  必要かつ有効なコード変更を行います。  
  
     詳細については、次を参照してください。 [Visual Basic エディット コンティニュでサポートされていない編集](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)します。  
  
    > [!NOTE]
    >  エディット コンティニュで許可されないコード変更を行おうとすると、編集部分の下に紫の波線が表示され、タスク一覧にタスクが表示されます。 この場合、無効なコード変更を元に戻さない限り、コードの実行を続行できません。  
  
3.  **デバッグ** メニューのをクリックして**続行**実行を再開します。  
  
     適用した編集がプロジェクトに取り込まれた状態でコードが実行されます。  
  
## <a name="see-also"></a>関連項目  
 [エディット コンティニュを Visual Basic でサポートされていない編集](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)   
 [エディット コンティニュ (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)



