---
title: Office プロジェクトのユーザー補助機能
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 99deac9a1a6587d345d288123029a5e3dde4308b
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865854"
---
# <a name="accessibility-in-office-projects"></a>Office プロジェクトのユーザー補助機能

Microsoft Visual Studio と Microsoft Office には、標準のユーザー補助の要件を満たすカスタム ソリューションを構築するための多くのユーザー補助機能が含まれます。 Microsoft では、Web 上のユーザー補助のガイドラインを公開します。 詳細については、次を参照してください。、[アクセシビリティ web サイト](http://go.microsoft.com/fwlink/?LinkID=37113)します。

ほとんどの場合は、Visual Studio での Office プロジェクトには、ユーザー補助の標準や公開プロパティ、ソリューションにアクセスできるようにするために設定できますが満たしています。 ただし、ユーザー補助機能が制限されている一部の機能があります。

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="accessibility-at-design-time"></a>デザイン時のユーザー補助

### <a name="use-shortcut-keys-in-document-level-projects"></a>ドキュメント レベルのプロジェクトのショートカット キーを使用します。
 Microsoft Office Word ドキュメントまたは Microsoft Office Excel ブックは、Visual Studio で開くが、一度に 1 つだけのアプリケーションは、ショートカット キーのコマンドを受け取ります。 既定では、Visual Studio がショートカット キー、すべてのコマンドを受け取りますが、Word または Excel ドキュメントにフォーカスがある場合は、選択して、受信を行うことができます**ダイナミック キーボード スキーム**上、**キーボード設定**ページ**オプション** ダイアログ ボックス。 詳細については、次を参照してください[Microsoft Office Word Keyboard、Microsoft Office Keyboard 設定のオプション ダイアログ ボックス](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)と[Microsoft Office Excel Keyboard、Microsoft Office Keyboard 設定、オプションダイアログボックス](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)。

### <a name="display-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>ドキュメント レベルのプロジェクトでリボンのショートカット キーを表示します。
 キーを押すことはできません、Word 文書または Excel ブックが Visual Studio で開いているとき、 **Alt**タブやリボン上のコントロールのショートカット キーを表示するキー。 文書またはブックがデザイナーで開いている間は、ショートカット キーを表示するには、次の手順を実行します。

#### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>デザイナーでリボン タブとコントロールのショートカット キーを表示するには

1.  Visual Studio での**ツール** メニューのをクリックして**オプション**します。

2.  展開、 **Office ツール**ノード、および選択**Microsoft Office Excel Keyboard**または**Microsoft Office Word Keyboard**必要に応じて、します。

3.  選択**ダイナミック キーボード スキーム**します。

     有効にする、変更の Visual Studio を再起動する必要があるかを示すメッセージが表示されます。

4.  **[OK]** をクリックします。

5.  Visual Studio を再起動して、プロジェクトを再度開きます。

6.  プロジェクトの文書またはブックのデザイナーを開きます。

7.  キーを押して**F6**リボンのショートカット キーを表示します。

## <a name="accessibility-at-runtime"></a>実行時に、ユーザー補助機能

### <a name="windows-forms-controls-on-office-documents"></a>Office ドキュメントでの Windows フォーム コントロール
 Windows フォーム コントロールは、スクリーン リーダーなどのユーザー補助機能するコントロールに関する情報を提供する、アクセシビリティのプロパティを公開します。 コントロールがドキュメント レベルのカスタマイズでの Office ドキュメントを上にある場合に、これらのアクセシビリティのプロパティの利用ができます。 詳細については、次を参照してください。 [Windows フォーム上のコントロールのアクセシビリティに関する情報を提供](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form)します。

 ただし、ユーザー補助な制限があります実行時に Windows フォーム コントロールは、Excel ブックまたは Word 文書にホストされている場合。

- 別に、1 つのコントロールからタブことはできません。

- 100% 以外に、ドキュメントのズーム設定を変更すると、ドキュメント上のコントロールが無効です。

  ドキュメントでの Windows フォーム コントロールの制限事項については、次を参照してください。[の制限事項の Windows フォーム コントロールの Office ドキュメント](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)します。

### <a name="actions-panes-and-custom-task-panes"></a>操作ウィンドウやカスタム作業ウィンドウ
 操作ウィンドウまたはカスタム作業ウィンドウにフォーカスが、コントロールにアクセスする、Windows フォーム アプリケーションのコントロールと同じようです。 [操作] ウィンドウとドキュメントの間にカーソルを移動するキーを押して**F6**します。

 操作ウィンドウやカスタム作業ウィンドウの詳細については、次を参照してください。[操作ウィンドウの概要](../vsto/actions-pane-overview.md)と[カスタム作業ウィンドウ](../vsto/custom-task-panes.md)します。

### <a name="display-modes"></a>表示モード

Visual Studio では、表示モードに関連する次の制限があります。

- 100% 以外に、ドキュメントのズーム設定を変更すると、Word 文書または Excel ワークシート上のコントロールが無効です。

- **新しいプロジェクト** ダイアログ ボックスが正しく表示されないコントロールをユーザーに、コンピューターのユーザー補助のオプションが変更された場合**ハイ コントラストを使用**します。

拡大鏡は、これらの制限を克服するために使用できます。 拡大鏡は、画面の一部を拡大して表示する別のウィンドウを作成します。 Windows での表示ユーティリティです。

## <a name="see-also"></a>関連項目

- [Office ソリューションを開発します。](../vsto/developing-office-solutions.md)
- [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)
- [障碍を持つユーザーのユーザー補助機能](../ide/reference/accessibility-for-people-with-disabilities.md)
- [Visual Studio のユーザー補助機能](../ide/reference/accessibility-features-of-visual-studio.md)