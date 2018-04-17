---
title: '方法: Office プロジェクトでイベント ハンドラーを作成 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Basic [Office development in Visual Studio], event handlers
- event handlers [Office development in Visual Studio]
- Visual C# [Office development in Visual Studio], event handlers
- events [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 833e41979d1dac9def7e647b396161d0ac5e2b67
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>方法: Office プロジェクトでイベント ハンドラーを作成する
  Visual Basic および c# でのイベント ハンドラーを作成するいくつかの方法はあります。 デザイン ビューで、コントロールをダブルクリックして既定のコントロールのイベント ハンドラーを作成またはの [イベント] ペインを使用して、**プロパティ**コントロール上の任意のイベントのハンドラーを作成するウィンドウです。 ただし、コード ビューでは、可能性がありますいない場合、イベント ハンドラーを作成する [デザイン] ビューに切り替えるにはします。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-create-an-event-handler-in-visual-basic"></a>Visual Basic では、イベント ハンドラーを作成するには  
  
1.  **クラス名**コード エディターの上部にあるドロップダウン リスト、選択するオブジェクトが、イベント ハンドラーを作成します。  
  
    > [!NOTE]  
    >  イベント ハンドラーを作成する場合は、`ThisDocument`または`ThisWorkbook`を選択する必要があります**(ThisDocument イベント)**または**(ThisWorkbook イベント)**で、**クラス名**ドロップダウン リスト  
  
2.  **メソッド名** ボックスで、コード エディターの上部には、イベントを選択します。  
  
     Visual Studio では、イベント ハンドラーを作成し、新しく作成されたイベント ハンドラーにカーソルを移動します。 イベント ハンドラーが既に存在する場合、カーソルは、既存のイベント ハンドラーに移動します。  
  
### <a name="to-create-an-event-handler-in-c"></a>C# の場合、イベント ハンドラーを作成するには  
  
1.  イベント デリゲートを作成、**スタートアップ**修飾イベント名の後にスペースを入力し、入力してクラスのイベント**+=**後にスペースをします。 例えば:  
  
     `this.<object name>.<event name> +=`  
  
2.  コードの行の末尾には、TAB キーを 2 回押します。  
  
     Visual Studio が自動的にコードの行を完了する、イベント ハンドラーを作成および挿入ポイントを新しく作成されたイベント ハンドラーに移動します。  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューションのコードの記述](../vsto/writing-code-in-office-solutions.md)   
 [チュートリアル: NamedRange コントロールのイベントのプログラミング](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Office ソリューションのビルド](../vsto/building-office-solutions.md)  
  
  