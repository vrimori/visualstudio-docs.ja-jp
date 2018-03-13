---
title: "VSTO アドインのパフォーマンスを向上させる |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: be5ec0d8e4654ad9d383278e5d0d60c7fa2e34c9
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="improving-the-performance-of-a-vsto-add-in"></a>VSTO アドインのパフォーマンスの向上
  Office アプリケーション用に作成した VSTO アドインを最適化して、そのアドインの開始、終了、また、項目を開くなどのタスクの実行を素早く行えるようにして、ユーザー エクスペリエンスを向上させることができます。 VSTO アドインが Outlook を対象にしている場合は、不十分なパフォーマンスが原因で VSTO アドインが無効にされる可能性を低くすることができます。 次の方針を導入すると、VSTO アドインのパフォーマンスを向上させることができます。  
  
-   [必要に応じた VSTO アドインの読み込み](#Load)。  
  
-   [Windows インストーラーを使用した Office ソリューションの発行](#Publish)。  
  
-   [リボン リフレクションのバイパス](#Bypass)。  
  
-   [負荷の高い操作を単独の実行スレッドで実行](#Perform)。  
  
 Outlook VSTO アドインを最適化する方法の詳細については、「 [アドインを有効に保つためのパフォーマンス基準](http://go.microsoft.com/fwlink/?LinkID=266503)」を参照してください。  
  
##  <a name="Load"></a> 必要に応じた VSTO アドインの読み込み  
 次の状況でのみ読み込まれるように VSTO アドインを構成できます。  
  
-   VSTO アドインのインストール後にユーザーがアプリケーションを初めて起動するとき。  
  
-   それ以降にアプリケーションを起動した後、ユーザーが初めて VSTO アドインを操作するとき。  
  
 たとえば、VSTO アドインの可能性がありますをワークシートに読み込むデータというラベルの付いたカスタム ボタンを選択したときに**自分のデータを取得**です。 **[自分のデータを取得]** ボタンがリボンに表示されるように、アプリケーションはこの VSTO アドインを少なくとも 1 回読み込む必要があります。 ただし、VSTO アドインは読み込まれません、ユーザーが次回アプリケーションを起動するとき。 VSTO アドインが読み込まれるのは、ユーザーが **[自分のデータを取得]** ボタンをクリックしたときのみです。  
  
#### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>必要に応じて VSTO アドインを読み込むように ClickOnce ソリューションを構成するには  
  
1.  **ソリューション エクスプローラー**で、プロジェクト ノードを選択します。  
  
2.  メニュー バーの **[表示]**、 **[プロパティ ページ]**の順にクリックします。  
  
3.  **[発行]** タブの **[オプション]** をクリックします。  
  
4.  **[発行オプション]** ダイアログ ボックスで、 **[Office の設定]** リスト項目を選択し、 **[必要に応じて読み込む]** オプションを選択してから、 **[OK]** をクリックします。  
  
#### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>必要に応じて VSTO アドインを読み込むように Windows インストーラー ソリューションを構成するには  
  
1.  レジストリで、設定、`LoadBehavior`のエントリ、*ルート*\Software\Microsoft\Office\\*ApplicationName*\Addins\\*add-in ID*キーを**0x10**です。  
  
     詳細については、「 [Registry Entries for VSTO Add-ins](../vsto/registry-entries-for-vsto-add-ins.md)」を参照してください。  
  
#### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>ソリューションのデバッグ中に必要に応じて VSTO アドインを読み込むようにソリューションを構成するには  
  
1.  設定するスクリプトを作成、`LoadBehavior`のエントリ、*ルート*\Software\Microsoft\Office\\*ApplicationName*\Addins\\*add-in ID*キーを**0x10**です。  
  
     このスクリプトの例を次のコードに示します。  
  
    ```  
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]  
    "Description"="MyAddIn"  
    "FriendlyName"="MyAddIn"  
    "LoadBehavior"=dword:00000010  
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"  
  
    ```  
  
2.  スクリプトを使用してレジストリを更新するビルド後のイベントを作成します。  
  
     次のコードに、ビルド後のイベントに追加できるコマンド文字列の例を示します。  
  
    ```  
    regedit /s "$(SolutionDir)$(SolutionName).reg"  
  
    ```  
  
     C# プロジェクトでビルド後のイベントを作成する方法については、次を参照してください。[する方法: ビルド イベントの指定 &#40;です。C# 35; &#41;](/visualstudio/ide/how-to-specify-build-events-csharp).  
  
     Visual Basic プロジェクトでビルド後のイベントを作成する方法については、次を参照してください。[する方法: ビルド イベントの指定 &#40;です。Visual Basic &#41;](/visualstudio/ide/how-to-specify-build-events-visual-basic).  
  
##  <a name="Publish"></a> Publish Office Solutions by Using Windows Installer  
 Windows インストーラーを使用してソリューションを発行する場合は、Visual Studio 2010 Tools for Office Runtime は、VSTO アドインを読み込むときに次の手順をスキップします。  
  
-   マニフェスト スキーマの検証。  
  
-   更新プログラムの自動的な確認。  
  
-   配置マニフェストのデジタル署名の検証。  
  
    > [!NOTE]  
    >  この方法は、ユーザーのコンピューター上の安全な場所に、VSTO アドインで展開する場合は必要ありません。  
  
 詳細については、「 [Windows インストーラーを使用した Office ソリューションの配置](../vsto/deploying-an-office-solution-by-using-windows-installer.md)」を参照してください。  
  
##  <a name="Bypass"></a> Bypass Ribbon Reflection  
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]を使用してソリューションをビルドする場合は、ソリューションを配置するときに、ユーザーが Visual Studio 2010 Tools for Office Runtime の最新バージョンを既にインストールしていることを確認します。 このランタイムの古いバージョンでは、リボンのカスタマイズを識別するために、ソリューションのアセンブリのリフレクションが実行されていました。 このプロセスを実行すると、VSTO アドインの読み込み速度がさらに低下する可能性があります。  
  
 別の方針として、Visual Studio 2010 Tools for Office Runtime のどのバージョンを使用する場合でも、リボンのカスタマイズを識別することを目的としたリフレクションを防止することもできます。 この方針に従うには、 `CreateRibbonExtensibility` メソッドをオーバーライドし、明示的にリボン オブジェクトを返します。 場合は、VSTO アドインで、リボンのカスタマイズが含まれていない、返す`null`メソッド内で。  
  
 次の例では、フィールドの値に基づいてリボン オブジェクトを返します。  
  
 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]  
  
##  <a name="Perform"></a> Perform Expensive Operations in a Separate Execution Thread  
 時間を要するタスク (長時間実行されるタスク、データベース接続、または他の種類のネットワークの呼び出しなど) を単独のスレッドで実行することを検討してください。 詳細については、「 [Threading Support in Office](../vsto/threading-support-in-office.md)」を参照してください。  
  
> [!NOTE]  
>  Office オブジェクト モデルを呼び出すすべてのコードは、メイン スレッドで実行する必要があります。  
  
## <a name="see-also"></a>参照  
 [VSTO アドインの必要に応じた読み込み](http://blogs.msdn.com/b/andreww/archive/2008/07/14/demand-loading-vsto-add-ins.aspx)   
 [Office アドインの CLR を遅延読み込み](http://blogs.msdn.com/b/andreww/archive/2008/04/19/delay-loading-the-clr-in-office-add-ins.aspx)   
 [VSTO のパフォーマンス: 遅延読み込みと開発者 (Stephen Peters)](http://blogs.msdn.com/b/vsto/archive/2010/01/07/vsto-performance-delay-loading-and-you.aspx)   
 [近日公開予定開発者 (Stephen Peters) の近くの Service Pack にパフォーマンスの向上](http://blogs.msdn.com/b/vsto/archive/2010/11/30/performance-improvements-coming-soon-to-a-service-pack-near-you-stephen-peters.aspx)   
 [VSTO のパフォーマンス: リボン リフレクション (Stephen Peters)](http://blogs.msdn.com/b/vsto/archive/2010/06/03/vsto-performance-ribbon-reflection.aspx)  
  
  