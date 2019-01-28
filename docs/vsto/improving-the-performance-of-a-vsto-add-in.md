---
title: VSTO アドインのパフォーマンスを向上させる
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a06022075086ad4792d35761c3af0e14f8f96e56
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867469"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>VSTO アドインのパフォーマンスを向上させる
  Office アプリケーション用に作成した VSTO アドインを最適化して、そのアドインの開始、終了、また、項目を開くなどのタスクの実行を素早く行えるようにして、ユーザー エクスペリエンスを向上させることができます。 VSTO アドインが Outlook を対象にしている場合は、不十分なパフォーマンスが原因で VSTO アドインが無効にされる可能性を低くすることができます。 次の方針を導入すると、VSTO アドインのパフォーマンスを向上させることができます。

- [必要に応じた VSTO アドインの読み込み](#Load)。

- [Windows インストーラーを使用した Office ソリューションの発行](#Publish)。

- [リボン リフレクションのバイパス](#Bypass)します。

- [負荷の高い操作を単独の実行スレッドで実行](#Perform)。

  Outlook VSTO アドインを最適化する方法の詳細については、次を参照してください。[を有効になっている VSTO アドインのパフォーマンス条件](http://go.microsoft.com/fwlink/?LinkID=266503)します。

##  <a name="Load"></a> 必要に応じた VSTO アドインの読み込み
 次の状況でのみ読み込まれるように VSTO アドインを構成できます。

- VSTO アドインのインストール後にユーザーがアプリケーションを初めて起動するとき。

- それ以降にアプリケーションを起動した後、ユーザーが初めて VSTO アドインを操作するとき。

  たとえば、VSTO アドインは、可能性がありますをワークシートに読み込むデータというラベルの付いたカスタム ボタンを選択したときに**マイ データの取得**。 アプリケーション、VSTO アドインには少なくとも 1 回との読み込みの必要がありますように、**マイ データの取得**ボタンがリボンに表示できます。 ただし、VSTO アドインは読み込まれません、ユーザーが次にアプリケーションを開始するときにします。 VSTO アドインが読み込まれるのは、ユーザーが **[自分のデータを取得]** ボタンをクリックしたときのみです。

### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>必要に応じて VSTO アドインを読み込むように ClickOnce ソリューションを構成するには

1.  **ソリューション エクスプローラー**で、プロジェクト ノードを選択します。

2.  メニュー バーで **[表示]** > **[プロパティ ページ]** の順に選びます。

3.  **[発行]** タブの **[オプション]** をクリックします。

4.  **[発行オプション]** ダイアログ ボックスで、 **[Office の設定]** リスト項目を選択し、 **[必要に応じて読み込む]** オプションを選択してから、 **[OK]** をクリックします。

### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>必要に応じて VSTO アドインを読み込むように Windows インストーラー ソリューションを構成するには

1.  レジストリで、設定、`LoadBehavior`のエントリ、 **_ルート_\Software\Microsoft\Office\\_ApplicationName_\Addins\\ _アドイン ID_** キー **0x10**します。

     詳細については、次を参照してください。 [VSTO アドインのレジストリ エントリ](../vsto/registry-entries-for-vsto-add-ins.md)します。

### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>ソリューションのデバッグ中に必要に応じて VSTO アドインを読み込むようにソリューションを構成するには

1.  設定するスクリプトを作成、`LoadBehavior`のエントリ、 **_ルート_\Software\Microsoft\Office\\_ApplicationName_\Addins\\ _アドイン ID_** キー **0x10**します。

     このスクリプトの例を次のコードに示します。

    ```cmd/sh
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]
    "Description"="MyAddIn"
    "FriendlyName"="MyAddIn"
    "LoadBehavior"=dword:00000010
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"

    ```

2.  スクリプトを使用してレジストリを更新するビルド後のイベントを作成します。

     次のコードに、ビルド後のイベントに追加できるコマンド文字列の例を示します。

    ```cmd/sh
    regedit /s "$(SolutionDir)$(SolutionName).reg"

    ```

     C# プロジェクトでビルド後イベントを作成する方法については、次を参照してください。[方法。ビルド イベントを指定&#40;C&#35;&#41;](../ide/how-to-specify-build-events-csharp.md)します。

     Visual Basic プロジェクトでビルド後のイベントを作成する方法については、次を参照してください。[方法。ビルド イベントを指定&#40;Visual Basic&#41;](../ide/how-to-specify-build-events-visual-basic.md)します。

##  <a name="Publish"></a> Windows インストーラーを使用して Office ソリューションを発行します。
 Windows インストーラーを使用してソリューションを発行する場合、Visual Studio 2010 Tools for Office ランタイムは、VSTO アドインが読み込まれるとき、次の手順を無視します。

- マニフェスト スキーマの検証。

- 更新プログラムの自動的な確認。

- 配置マニフェストのデジタル署名の検証。

  > [!NOTE]
  >  このアプローチは、ユーザーのコンピューター上のセキュリティで保護された場所に、VSTO アドインを展開する場合は必要ありません。

  詳細については、次を参照してください。 [Windows インストーラーを使用して Office ソリューションを配置](../vsto/deploying-an-office-solution-by-using-windows-installer.md)します。

##  <a name="Bypass"></a> リボン リフレクションをバイパスします。
 使用してソリューションをビルドする場合[!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]ソリューションを展開するときに、ユーザーが、Visual Studio 2010 Tools for Office ランタイムの最新バージョンをインストールがあることを確認します。 リボンのカスタマイズを検索するアセンブリをソリューションに、そのランタイムの以前のバージョンが反映されます。 このプロセスを実行すると、VSTO アドインの読み込み速度がさらに低下する可能性があります。

 代わりに、リボンのカスタマイズを識別するためにリフレクションを使用してから、Visual Studio 2010 Tools for Office ランタイムの任意のバージョンを防ぐことができます。 この方法には、オーバーライド、`CreateRibbonExtensibility`メソッド、およびリボン オブジェクトを明示的に返します。 返す場合は、VSTO アドインのリボンのカスタマイズが含まれていない、`null`メソッド内で。

 次の例では、フィールドの値に基づいてリボン オブジェクトを返します。

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]

##  <a name="Perform"></a> 個別の実行スレッドで高価な操作を実行します。
 時間を要するタスク (長時間実行されるタスク、データベース接続、または他の種類のネットワークの呼び出しなど) を単独のスレッドで実行することを検討してください。 詳細については、次を参照してください。[のスレッドの Office でサポート](../vsto/threading-support-in-office.md)します。

> [!NOTE]
>  Office オブジェクト モデルを呼び出すすべてのコードは、メイン スレッドで実行する必要があります。

## <a name="see-also"></a>関連項目

- [要求時に読み込む VSTO アドイン](https://blogs.msdn.microsoft.com/andreww/2008/07/14/demand-loading-vsto-add-ins/)
- [Office アドイン内での CLR の遅延読み込み](https://blogs.msdn.microsoft.com/andreww/2008/04/19/delay-loading-the-clr-in-office-add-ins/)
- [Visual Studio を使用して Office 用 VSTO アドインの作成します。](create-vsto-add-ins-for-office-by-using-visual-studio.md)
