---
title: Office プロジェクトのユーザー補助機能
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, accessibility
- shortcut keys [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], shortcut keys
- accessibility [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 34a1ea090e85168b5fd0bf2e55c22d0a38ff331f
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="accessibility-in-office-projects"></a>Office プロジェクトのユーザー補助機能
  Microsoft Visual Studio と Microsoft Office を使用すると、標準のユーザー補助の要件を満たすカスタム ソリューションをビルドする多くのユーザー補助機能が含まれます。 Microsoft では、Web 上のユーザー補助のためのガイドラインを発行します。 詳細については、次を参照してください。、[アクセシビリティ web サイト](http://go.microsoft.com/fwlink/?LinkID=37113)です。  

 ほとんどの場合は、Visual Studio での Office プロジェクトには、アクセシビリティ標準または公開のプロパティをソリューションがアクセスできるように設定することができますが満たしています。 ただし、これにはユーザー補助機能が限られている一部の機能があります。  

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  

## <a name="accessibility-at-design-time"></a>デザイン時のユーザー補助  

### <a name="use-shortcut-keys-in-document-level-projects"></a>ドキュメント レベルのプロジェクトで使用するショートカット キー  
 Microsoft Office Word ドキュメントまたは Microsoft Office Excel ブックが Visual Studio で開いている場合、一度に 1 つだけのアプリケーションは、ショートカット キーのコマンドを受信します。 既定では、Visual Studio はすべてのショートカット キー コマンドを受け取りますが、Word または Excel のドキュメントにフォーカスがある場合を選択して、それらを受信することができます**ダイナミック キーボード スキーム**上、 **Keyboard 設定**ページ**オプション** ダイアログ ボックス。 詳細については、次を参照してください[Microsoft Office Word Keyboard、Microsoft Office Keyboard 設定のオプション ダイアログ ボックス](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)と[Microsoft Office Excel Keyboard、Microsoft Office Keyboard 設定、オプションダイアログボックス](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)。  

### <a name="display-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>ドキュメント レベルのプロジェクトのリボンのショートカット キーを表示します。  
 キーを押すことはできません、Word 文書または Excel ブックが Visual Studio で開いているとき、 **Alt**タブやリボン コントロールのショートカット キーを表示するキー。 文書またはブックがデザイナーで開いている間は、ショートカット キーを表示するには、次の手順を実行します。  

#### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>デザイナーでリボン タブやコントロールのショートカット キーを表示するには  

1.  Visual Studio での**ツール** メニューのをクリックして**オプション**です。  

2.  展開、 **Office ツール**ノード、および選択**Microsoft Office Excel Keyboard**または**Microsoft Office Word Keyboard** をクリックします。  

3.  選択**ダイナミック キーボード スキーム**です。  

     有効に変更するために Visual Studio を再起動する必要があるかを示すメッセージが表示されます。  

4.  **[OK]** をクリックします。  

5.  Visual Studio を再起動し、プロジェクトを再度開きます。  

6.  プロジェクトの文書またはブックのデザイナーを開きます。  

7.  キーを押して**F6**をリボンのショートカット キーを表示します。  

## <a name="accessibility-at-runtime"></a>実行時にユーザー補助機能  

### <a name="windows-forms-controls-on-office-documents"></a>Office ドキュメントでの Windows フォーム コントロール  
 Windows フォーム コントロールは、スクリーン リーダーなどのユーザー補助機能に、コントロールに関する情報を提供するユーザー補助プロパティを公開します。 コントロールがドキュメント レベルのカスタマイズでの Office ドキュメントにある場合に、これらのユーザー補助機能プロパティの利用ができます。 詳細については、次を参照してください。 [Windows フォームのコントロールのアクセシビリティ情報を提供](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form)です。  

 ただし、ユーザー補助な制限があります実行時に Excel ブックまたは Word 文書で Windows フォーム コントロールがホストされている場合。  

-   1 つのコントロールから タブの別にすることはできません。  

-   100% 以外に、ドキュメントのズーム設定を変更すると、文書のコントロールが無効です。  

 ドキュメント上で Windows フォーム コントロールの制限については、次を参照してください。[制限事項の Windows フォーム コントロールでの Office ドキュメント](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)です。  

### <a name="actions-panes-and-custom-task-panes"></a>操作ウィンドウやカスタム作業ウィンドウ  
 [操作] ウィンドウまたはカスタム作業ウィンドウにはフォーカスがあるときにコントロールにアクセスする、Windows フォーム アプリケーションのコントロールと同じようです。 [操作] ウィンドウとドキュメントの間にカーソルを移動するにキーを押します**F6**です。  

 操作ウィンドウやカスタム作業ウィンドウの詳細については、次を参照してください。[操作ウィンドウの概要](../vsto/actions-pane-overview.md)と[カスタム作業ウィンドウの](../vsto/custom-task-panes.md)します。  

### <a name="display-modes"></a>表示モード  
 Visual Studio では、表示モードに関連する次の制限があります。  

-   100% 以外に、ドキュメントのズーム設定を変更すると、Word 文書や Excel ワークシートでコントロールが無効です。  

-   **新しいプロジェクト** ダイアログ ボックスが正しく表示されませんコントロール、ユーザーに、コンピューターのユーザー補助のオプションが変更された場合**を使用してハイ コントラスト**です。  

 拡大鏡を使用して、これらの制約を克服することができます。 拡大鏡は、画面の一部を拡大表示する別のウィンドウを作成する Windows の表示ユーティリティです。  

## <a name="see-also"></a>関連項目  
 [Office ソリューションを開発します。](../vsto/developing-office-solutions.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [障碍を持つユーザー補助機能](/visualstudio/ide/reference/accessibility-for-people-with-disabilities)   
 [Visual Studio のユーザー補助機能](/visualstudio/ide/reference/accessibility-features-of-visual-studio)  
