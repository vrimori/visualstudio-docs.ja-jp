---
title: "VSTO アドインのパフォーマンスの向上 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 03ef25c2-6308-4737-a655-74bbbb472dc2
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# VSTO アドインのパフォーマンスの向上
  Office アプリケーション用に作成した VSTO アドインを最適化して、そのアドインの開始、終了、また、項目を開くなどのタスクの実行を素早く行えるようにして、ユーザー エクスペリエンスを向上させることができます。 VSTO アドインが Outlook を対象にしている場合は、不十分なパフォーマンスが原因で VSTO アドインが無効にされる可能性を低くすることができます。 次の方針を導入すると、VSTO アドインのパフォーマンスを向上させることができます。  
  
-   [必要に応じた VSTO アドインの読み込み](#Load)。  
  
-   [Windows インストーラーを使用した Office ソリューションの発行](#Publish)。  
  
-   [リボン リフレクションのバイパス](#Bypass)。  
  
-   [負荷の高い操作を単独の実行スレッドで実行](#Perform)。  
  
 Outlook VSTO アドインを最適化する方法の詳細については、「[アドインを有効に保つためのパフォーマンス基準](http://go.microsoft.com/fwlink/?LinkID=266503)」を参照してください。  
  
##  <a name="Load"></a> 必要に応じた VSTO アドインの読み込み  
 次の状況でのみ読み込まれるように VSTO アドインを構成できます。  
  
-   VSTO アドインのインストール後にユーザーがアプリケーションを初めて起動するとき。  
  
-   それ以降にアプリケーションを起動した後、ユーザーが初めて VSTO アドインを操作するとき。  
  
 たとえば、ユーザーが **\[自分のデータを取得\]** というラベルの付いたカスタム ボタンをクリックしたときにワークシートにデータを取り込む VSTO アドインがあるとします。**\[自分のデータを取得\]** ボタンがリボンに表示されるように、アプリケーションはこの VSTO アドインを少なくとも 1 回読み込む必要があります。 ただし、ユーザーが次にアプリケーションを起動するときには、この VSTO アドインは読み込まれません。 VSTO アドインが読み込まれるのは、ユーザーが **\[自分のデータを取得\]** ボタンをクリックしたときのみです。  
  
#### 必要に応じて VSTO アドインを読み込むように ClickOnce ソリューションを構成するには  
  
1.  **ソリューション エクスプローラー**で、プロジェクト ノードを選択します。  
  
2.  メニュー バーの **\[表示\]**、**\[プロパティ ページ\]** の順にクリックします。  
  
3.  **\[発行\]** タブの **\[オプション\]** をクリックします。  
  
4.  **\[発行オプション\]** ダイアログ ボックスで、**\[Office の設定\]** リスト項目を選択し、**\[必要に応じて読み込む\]** オプションを選択してから、**\[OK\]** をクリックします。  
  
#### 必要に応じて VSTO アドインを読み込むように Windows インストーラー ソリューションを構成するには  
  
1.  レジストリで、*Root*\\Software\\Microsoft\\Office\\*ApplicationName*\\Addins\\*Add\-in ID* キーの `LoadBehavior` エントリを **0x10** に設定します。  
  
     詳細については、「[VSTO アドインのレジストリ エントリ](../vsto/registry-entries-for-vsto-add-ins.md)」を参照してください。  
  
#### ソリューションのデバッグ中に必要に応じて VSTO アドインを読み込むようにソリューションを構成するには  
  
1.  *Root*\\Software\\Microsoft\\Office\\*ApplicationName*\\Addins\\*Add\-in ID* キーの `LoadBehavior` エントリを **0x10** に設定するスクリプトを作成します。  
  
     このスクリプトの例を次のコードに示します。  
  
    ```  
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn] "Description"="MyAddIn" "FriendlyName"="MyAddIn" "LoadBehavior"=dword:00000010 "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"  
  
    ```  
  
2.  スクリプトを使用してレジストリを更新するビルド後のイベントを作成します。  
  
     次のコードに、ビルド後のイベントに追加できるコマンド文字列の例を示します。  
  
    ```  
    regedit /s "$(SolutionDir)$(SolutionName).reg"  
  
    ```  
  
     C\# プロジェクト内でビルド後のイベントを作成する方法の詳細については、「[方法 : ビルド イベントを指定する &#40;C&#35;&#41;](../Topic/How%20to:%20Specify%20Build%20Events%20(C%23).md)」を参照してください。  
  
     Visual Basic プロジェクト内でビルド後のイベントを作成する方法の詳細については、「[方法 : ビルド イベントを指定する &#40;C&#35;&#41;](../Topic/How%20to:%20Specify%20Build%20Events%20(C%23).md)」を参照してください。  
  
##  <a name="Publish"></a> Windows インストーラーを使用した Office ソリューションの発行  
 Windows インストーラーを使用してソリューションを発行する場合は、Visual Studio 2010 Tools for Office Runtime は、VSTO アドインを読み込むときに次の手順をスキップします。  
  
-   マニフェスト スキーマの検証。  
  
-   更新プログラムの自動的な確認。  
  
-   配置マニフェストのデジタル署名の検証。  
  
    > [!NOTE]  
    >  このアプローチは、ユーザーのコンピューターの安全な場所に VSTO アドインを配置する場合は不要です。  
  
 詳細については、「[Windows インストーラーを使用した Office ソリューションの配置](../vsto/deploying-an-office-solution-by-using-windows-installer.md)」を参照してください。  
  
##  <a name="Bypass"></a> リボン リフレクションのバイパス  
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]を使用してソリューションをビルドする場合は、ソリューションを配置するときに、ユーザーが Visual Studio 2010 Tools for Office Runtime の最新バージョンを既にインストールしていることを確認します。 このランタイムの古いバージョンでは、リボンのカスタマイズを識別するために、ソリューションのアセンブリのリフレクションが実行されていました。 このプロセスを実行すると、VSTO アドインの読み込み速度がさらに低下する可能性があります。  
  
 別の方針として、Visual Studio 2010 Tools for Office Runtime のどのバージョンを使用する場合でも、リボンのカスタマイズを識別することを目的としたリフレクションを防止することもできます。 この方針に従うには、`CreateRibbonExtensibility` メソッドをオーバーライドし、明示的にリボン オブジェクトを返します。 VSTO アドインにリボンのカスタマイズが何も含まれていない場合は、メソッド内で `null` を返します。  
  
 次の例では、フィールドの値に基づいてリボン オブジェクトを返します。  
  
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Choose_Ribbon/CS/ThisWorkbook.cs#1)]
 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Choose_Ribbon/VB/ThisWorkbook.vb#1)]  
  
##  <a name="Perform"></a> 負荷の高い操作を単独の実行スレッドで実行  
 時間を要するタスク \(長時間実行されるタスク、データベース接続、または他の種類のネットワークの呼び出しなど\) を単独のスレッドで実行することを検討してください。 詳細については、「[Office でのスレッドのサポート](../vsto/threading-support-in-office.md)」を参照してください。  
  
> [!NOTE]  
>  Office オブジェクト モデルを呼び出すすべてのコードは、メイン スレッドで実行する必要があります。  
  
## 参照  
 [VSTO アドインの必要に応じた読み込み](http://blogs.msdn.com/b/andreww/archive/2008/07/14/demand-loading-vsto-add-ins.aspx)   
 [Office アドイン内での CLR の遅延読み込み](http://blogs.msdn.com/b/andreww/archive/2008/04/19/delay-loading-the-clr-in-office-add-ins.aspx)   
 [VSTO のパフォーマンス: 遅延読み込みと開発者 \(Stephen Peters\)](http://blogs.msdn.com/b/vsto/archive/2010/01/07/vsto-performance-delay-loading-and-you.aspx)   
 [近日公開予定の Service Pack によるパフォーマンスの向上 \(Stephen Peters\)](http://blogs.msdn.com/b/vsto/archive/2010/11/30/performance-improvements-coming-soon-to-a-service-pack-near-you-stephen-peters.aspx)   
 [VSTO のパフォーマンス: リボン リフレクション \(Stephen Peters\)](http://blogs.msdn.com/b/vsto/archive/2010/06/03/vsto-performance-ribbon-reflection.aspx)  
  
  