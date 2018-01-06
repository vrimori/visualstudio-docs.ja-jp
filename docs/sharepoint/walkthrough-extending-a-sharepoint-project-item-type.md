---
title: "チュートリアル: SharePoint プロジェクト項目の種類の拡張 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
ms.assetid: 1cea4e0f-ce33-4cd7-a664-800184865456
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: c885fe006f1a6a65f97b1f11de61e0639dd1559a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-extending-a-sharepoint-project-item-type"></a>チュートリアル: SharePoint プロジェクト項目の種類の拡張
  使用することができます、**ビジネス データ接続モデル**プロジェクト アイテムを SharePoint でビジネス データ接続 (BDC) サービスのモデルを作成します。 既定では、このプロジェクト項目を使用してモデルを作成しただけでは、モデル内のデータがユーザーに表示されません。 ユーザーがデータを閲覧できるようにするには、それに加えて、SharePoint に外部リストを作成する必要があります。  
  
 このチュートリアルでは、拡張機能を作成します、**ビジネス データ接続モデル**プロジェクト項目です。 開発者は、この拡張機能を使用することで、BDC モデルのデータを表示するための外部リストを同じプロジェクト内で作成できます。 このチュートリアルでは、次のタスクについて説明します。  
  
-   次の 2 つの主要タスクを実行する Visual Studio の拡張機能を作成する。  
  
    -   BDC モデル内のデータを表示するための外部リストを生成する。 この拡張機能は、リストを定義する Elements.xml ファイルを、SharePoint プロジェクト システムのオブジェクト モデルを使用して生成します。 さらに、BDC モデルと一緒に配置できるように、このファイルをプロジェクトに追加します。  
  
    -   ショートカット メニュー項目を追加、**ビジネス データ接続モデル**内の項目をプロジェクト**ソリューション エクスプ ローラー**です。 開発者は、このメニュー項目をクリックして、BDC モデル用の外部リストを生成できます。  
  
-   拡張機能のアセンブリを配置するための Visual Studio Extension (VSIX) パッケージを構築する。  
  
-   拡張機能をテストする。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、開発コンピューターに次のコンポーネントが必要です。  
  
-   サポート対象エディションの Microsoft Windows、SharePoint、および Visual Studio。 詳細については、次を参照してください。 [SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)です。  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。 このチュートリアルでは、 **VSIX プロジェクト**sdk をプロジェクト項目を配置するための VSIX パッケージを作成するテンプレートです。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツール拡張](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)です。  
  
 次の概念に関する知識があると役に立ちますが、チュートリアルを実行するうえで必須というわけではありません。  
  
-   [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] の BDC サービス。 詳細については、次を参照してください。 [BDC アーキテクチャ](http://go.microsoft.com/fwlink/?LinkId=177798)です。  
  
-   BDC モデルの XML スキーマ。 詳細については、次を参照してください。 [BDC モデル インフラストラクチャ](http://go.microsoft.com/fwlink/?LinkId=177799)です。  
  
## <a name="creating-the-projects"></a>プロジェクトの作成  
 このチュートリアルを完了するには、2 つのプロジェクトを作成する必要があります。  
  
-   プロジェクト項目の拡張機能を配置するために VSIX パッケージを作成する VSIX プロジェクト。  
  
-   プロジェクト項目の拡張機能を実装するクラス ライブラリ プロジェクト。  
  
 この 2 つのプロジェクトを作成することから始めます。  
  
#### <a name="to-create-the-vsix-project"></a>VSIX プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]**の順にクリックします。  
  
3.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual c#**または**Visual Basic** 、ノードを選択し、 **Extensibility**ノード。  
  
    > [!NOTE]  
    >  **Extensibility**ノードは、Visual Studio SDK をインストールする場合にのみ使用できます。 詳細については、このトピックで前に説明した「前提条件」を参照してください。  
  
4.  上部にある一覧で、**新しいプロジェクト** ダイアログ ボックスで、選択**.NET Framework 4.5**です。  
  
     SharePoint ツールの拡張機能を使用するには、このバージョンの .NET Framework の機能が必要です。  
  
5.  選択、 **VSIX プロジェクト**テンプレート。  
  
6.  **名前**ボックスに、入力**GenerateExternalDataLists**を選択し、 **OK**ボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]追加、 **GenerateExternalDataLists**プロジェクトを**ソリューション エクスプ ローラー**です。  
  
7.  Source.extension.vsixmanifest ファイルに自動的に表示されない場合で、GenerateExternalDataLists プロジェクトのショートカット メニューを開きし、**を開く**  
  
8.  source.extension.vsixmanifest ファイルで [作成者] フィールドが空白でないことを確認し (「Contoso」と入力し)、ファイルを保存して閉じます。  
  
#### <a name="to-create-the-extension-project"></a>拡張機能プロジェクトを作成するには  
  
1.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **GenerateExternalDataLists**ソリューション ノードを選択して**追加**を選択し**新しいプロジェクト**.  
  
2.  **新しいプロジェクトの追加** ダイアログ ボックスで、展開、 **Visual c#**または**Visual Basic** 、ノードを選択し、 **Windows**ノード。  
  
3.  ダイアログ ボックスの上部にある一覧で選択**.NET Framework 4.5**です。  
  
4.  プロジェクト テンプレートの一覧で選択**クラス ライブラリ**です。  
  
5.  **名前**ボックスに、入力**BdcProjectItemExtension**を選択し、 **OK**ボタンをクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]追加、 **BdcProjectItemExtension**プロジェクトがソリューションにし、既定の Class1 コード ファイルを開きます。  
  
6.  Class1 コード ファイルをプロジェクトから削除します。  
  
## <a name="configuring-the-extension-project"></a>拡張機能プロジェクトの構成  
 プロジェクト項目の拡張機能を作成するためのコードを記述する前に、コード ファイルおよびアセンブリ参照を拡張プロジェクトに追加します。  
  
#### <a name="to-configure-the-project"></a>プロジェクトを構成するには  
  
1.  BdcProjectItemExtension プロジェクトに、次の名前を持つ 2 つのコード ファイルを追加します。  
  
    -   ProjectItemExtension  
  
    -   GenerateExternalDataLists  
  
2.  BdcProjectItemExtension プロジェクトを選択し、メニュー バーで、次のように選択します。**プロジェクト**、**参照の追加**です。  
  
3.  下にある、**アセンブリ** ノードを選択して、 **Framework**ノードを展開し、次のアセンブリの各チェック ボックスをオン。  
  
    -   System.ComponentModel.Composition  
  
    -   WindowsBase  
  
4.  下にある、**アセンブリ** ノードを選択、**拡張**ノードをクリックし、チェック ボックスは次のアセンブリの。  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  **[OK]** を選択します。  
  
## <a name="defining-the-project-item-extension"></a>プロジェクト項目の拡張機能の定義  
 拡張機能を定義するクラスを作成、**ビジネス データ接続モデル**プロジェクト項目です。 拡張機能を定義するため、このクラスに <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> インターフェイスを実装します。 このインターフェイスは、既存の種類のプロジェクト項目を拡張する場合に必ず実装します。  
  
#### <a name="to-define-the-project-item-extension"></a>プロジェクト項目の拡張機能を定義するには  
  
1.  次のコードを ProjectItemExtension コード ファイルに貼り付けます。  
  
    > [!NOTE]  
    >  このコードを追加した直後は、いくつかのコンパイル エラーが発生します。 これらのエラーは、この後の手順でコードを追加すると解消されます。  
  
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/projectitemextension.cs#1)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/projectitemextension.vb#1)]  
  
## <a name="creating-the-external-data-lists"></a>外部データ リストの作成  
 BDC モデル内の各エンティティの外部データ リストを作成する `GenerateExternalDataListsExtension` クラスの部分定義を追加します。 外部データ リストを作成するために、このコードはまず BDC モデル ファイル内の XML データを解析して、BDC モデルのエンティティ データを読み取ります。 次に、BDC モデルに基づくリスト インスタンスを作成し、このリスト インスタンスをプロジェクトに追加します。  
  
#### <a name="to-create-the-external-data-lists"></a>外部データ リストを作成するには  
  
1.  次のコードを GenerateExternalDataLists コード ファイルに貼り付けます。  
  
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.cs#2)]  
  
## <a name="checkpoint"></a>チェックポイント  
 この段階で、プロジェクト項目の拡張機能に必要なすべてのコードがプロジェクトに揃ったことになります。 エラーが発生することなくプロジェクトをコンパイルできるかどうか、ソリューションをビルドして確認してください。  
  
#### <a name="to-build-the-solution"></a>ソリューションをビルドするには  
  
1.  メニュー バーの **[ビルド]**、 **[ソリューションのビルド]**の順にクリックします。  
  
## <a name="creating-a-vsix-package-to-deploy-the-project-item-extension"></a>プロジェクト項目の拡張機能を配置するための VSIX パッケージの作成  
 拡張機能を配置するには、ソリューションで VSIX プロジェクトを使用して VSIX パッケージを作成します。 まず、VSIX プロジェクトに含まれている source.extension.vsixmanifest ファイルを変更して、VSIX パッケージを構成します。 次に、ソリューションをビルドして VSIX パッケージを作成します。  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>VSIX パッケージを構成および作成するには  
  
1.  **ソリューション エクスプ ローラー**GenerateExternalDataLists プロジェクトの source.extension.vsixmanifest ファイルのショートカット メニューを開くしを選択し、**開く**です。  
  
     Visual Studio によってマニフェスト エディターでファイルが開きます。 source.extension.vsixmanifest ファイルが、すべての VSIX パッケージで必要とされる extension.vsixmanifest ファイルの基礎となります。 このファイルの詳細については、次を参照してください。 [VSIX 拡張機能スキーマ 1.0 リファレンス](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)です。  
  
2.  **Product Name**ボックスに、入力**External Data List Generator**です。  
  
3.  **作成者**ボックスに、入力**Contoso**です。  
  
4.  **説明**ボックスに、入力**の拡張機能を外部データ リストを生成するために使用するビジネス データ接続モデル プロジェクト項目を**です。  
  
5.  **資産** タブ、エディターの選択、**新規**ボタンをクリックします。  
  
     **新しいアセットの追加** ダイアログ ボックスが表示されます。  
  
6.  **型**一覧で、選択**Microsoft.VisualStudio.MefComponent**です。  
  
    > [!NOTE]  
    >  この値は、extension.vsixmanifest ファイル内の `MefComponent` 要素に対応します。 この要素は、VSIX パッケージ内の拡張機能アセンブリの名前を指定します。 詳細については、次を参照してください。 [MEFComponent 要素 (VSX Schema)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551)です。  
  
7.  **ソース**一覧で、選択**現在のソリューション内のプロジェクト**です。  
  
8.  **プロジェクト**一覧で、選択**BdcProjectItemExtension**を選択し、 **OK**ボタンをクリックします。  
  
9. メニュー バーの **[ビルド]**、 **[ソリューションのビルド]**の順にクリックします。  
  
10. エラーが発生することなくプロジェクトがコンパイルされてビルドされたことを確認します。  
  
11. GenerateExternalDataLists プロジェクトのビルド出力フォルダーに GenerateExternalDataLists.vsix ファイルが格納されていることを確認します。  
  
     既定では、ビルド出力フォルダーは ..\bin\Debug で、プロジェクト ファイルが格納されているフォルダーの下にあります。  
  
## <a name="testing-the-project-item-extension"></a>プロジェクト項目の拡張機能のテスト  
 これで、プロジェクト項目の拡張機能をテストする準備ができました。 まず、Visual Studio の実験用インスタンスで拡張機能プロジェクトのデバッグを開始します。 次に、Visual Studio の実験用インスタンスで拡張機能を使用して、BDC モデルの外部リストを生成します。 最後に、SharePoint サイトで外部リストを開いて正常に動作するかどうかを確認します。  
  
#### <a name="to-start-debugging-the-extension"></a>拡張機能のデバッグを開始するには  
  
1.  必要に応じて、管理者の資格情報を使用して Visual Studio を再起動し、GenerateExternalDataLists ソリューションを開きます。  
  
2.  BdcProjectItemExtension プロジェクトで、ProjectItemExtension コード ファイルを開き、`Initialize` メソッド内のコード行にブレークポイントを追加します。  
  
3.  GenerateExternalDataLists コード ファイルを開き、`GenerateExternalDataLists_Execute` メソッドのコードの先頭行にブレークポイントを追加します。  
  
4.  選択して、F5 キーを選択して、または、メニュー バーでのデバッグを開始**デバッグ**、**デバッグの開始**です。  
  
     Visual Studio によって、拡張機能が %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\External Data List Generator\1.0 にインストールされ、Visual Studio の実験用インスタンスが開始されます。 このインスタンスの Visual Studio でプロジェクト項目をテストします。  
  
#### <a name="to-test-the-extension"></a>拡張機能をテストするには  
  
1.  Visual Studio の実験用インスタンスのメニュー バーで、次のように選択します。**ファイル**、**新規**、**プロジェクト**です。  
  
2.  **新しいプロジェクト** ダイアログ ボックスで、展開、**テンプレート** ノードを展開、 **Visual c#**ノード、展開、 **SharePoint**ノード、し、選択**2010**です。  
  
3.  一覧で、ダイアログ ボックスの上部にあることを確認**.NET Framework 3.5**が選択されています。 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] のプロジェクトには、このバージョンの .NET Framework が必要です。  
  
4.  プロジェクト テンプレートの一覧で選択**SharePoint 2010 プロジェクト**です。  
  
5.  **名前**ボックスに、入力**SharePointProjectTestBDC**を選択し、 **OK**ボタンをクリックします。  
  
6.  SharePoint カスタマイズ ウィザードで、デバッグに使用を選択する場合、サイトの URL を入力してください。**ファーム ソリューションとして配置**、を選択し、**完了**ボタンをクリックします。  
  
7.  SharePointProjectTestBDC プロジェクトのショートカット メニューを開き、選択**追加**を選択し**新しい項目の**します。  
  
8.  **新しい項目の追加 - SharePointProjectTestBDC**  ダイアログ ボックスで、インストールされている言語ノードを展開し、展開、 **SharePoint**ノード。  
  
9. 選択、 **2010**  ノードを選択し、**ビジネス データ接続モデル (ファーム ソリューションのみ)**テンプレート。  
  
10. **名前**ボックスに、入力**TestBDCModel**を選択し、**追加**ボタンをクリックします。  
  
11. Visual Studio のもう一方のインスタンスで、ProjectItemExtension コード ファイルの `Initialize` メソッドに設定したブレークポイントで、コードが停止していることを確認します。  
  
12. Visual Studio の停止中のインスタンスで、 **f5 キーを押して**キー、または、メニュー バーで、次のように選択します。**デバッグ**、**続行**プロジェクトのデバッグを続行します。  
  
13. Visual Studio の実験用インスタンスの選択、 **f5 キーを押して**キー、または、メニュー バーで、次のように選択します**デバッグ**、**デバッグの開始**をビルド、配置、および実行、  **。TestBDCModel**プロジェクト。  
  
     デバッグ用に指定した SharePoint サイトの既定のページが Web ブラウザーに表示されます。  
  
14. いることを確認、**一覧**クイック起動領域のセクションでは、プロジェクトの既定の BDC モデルに基づいているリストにまだ存在しません。 まず、SharePoint のユーザー インターフェイスを使用するか、プロジェクト項目の拡張機能を使用して、外部データ リストを作成する必要があります。  
  
15. Web ブラウザーを閉じます。  
  
16. TestBDCModel プロジェクトを開いている Visual Studio のインスタンスでのショートカット メニューを開き、 **TestBDCModel**内のノード**ソリューション エクスプ ローラー**を選択し**外部データの生成リスト**です。  
  
17. Visual Studio のもう一方のインスタンスで、`GenerateExternalDataLists_Execute` メソッドに設定したブレークポイントで、コードが停止していることを確認します。 選択、 **f5 キーを押して**キー、または、メニュー バーで、次のように選択します。**デバッグ**、**続行**プロジェクトのデバッグを続行します。  
  
18. Visual Studio の実験用インスタンスはというリスト インスタンスが追加**Entity1DataList**するによって、TestBDCModel プロジェクト、およびインスタンスも生成されますがという名前のフィーチャー **Feature2**一覧については、インスタンス。  
  
19. 選択、 **f5 キーを押して**キー、または、メニュー バーで、次のように選択します。**デバッグ**、**デバッグの開始**をビルド、配置、および、TestBDCModel プロジェクトを実行します。  
  
     デバッグに使用する SharePoint サイトの既定のページが Web ブラウザーに表示されます。  
  
20. **一覧**セクション、クイック起動領域の選択、 **Entity1DataList**  ボックスの一覧です。  
  
21. リストに Identifier1 および Message という名前の列が存在し、項目 (Identifier1 の値は 0 で、Message の値は Hello World) が 1 つ含まれていることを確認します。  
  
     **ビジネス データ接続モデル**プロジェクト テンプレートは、すべてのデータを提供する既定の BDC モデルを生成します。  
  
22. Web ブラウザーを閉じます。  
  
## <a name="cleaning-up-the-development-computer"></a>開発コンピューターのクリーンアップ  
 プロジェクト項目の拡張機能のテストが終わったら、外部リストおよび BDC モデルを SharePoint サイトから削除し、さらにプロジェクト項目の拡張機能を Visual Studio から削除します。  
  
#### <a name="to-remove-the-external-data-list-from-the-sharepoint-site"></a>SharePoint サイトから外部データ リストを削除するには  
  
1.  SharePoint サイトのクイック起動領域で、選択、 **Entity1DataList**  ボックスの一覧です。  
  
2.  SharePoint サイトのリボンで、選択、**リスト**タブです。  
  
3.  **リスト** タブで、**設定**グループで、選択**一覧の設定**です。  
  
4.  **権限と管理**を選択**このリストの削除**を選択し**ok**をごみ箱にリストを送信することを確認します。  
  
5.  Web ブラウザーを閉じます。  
  
#### <a name="to-remove-the-bdc-model-from-the-sharepoint-site"></a>BDC モデルを SharePoint サイトから削除するには  
  
1.  Visual Studio の実験用インスタンスのメニュー バーで、次のように選択します。**ビルド**、 **Retract**です。  
  
     Visual Studio によって BDC モデルが SharePoint サイトから削除されます。  
  
#### <a name="to-remove-the-project-item-extension-from-visual-studio"></a>プロジェクト項目の拡張機能を Visual Studio から削除するには  
  
1.  Visual Studio の実験用インスタンスのメニュー バーで、次のように選択します。**ツール**、**拡張機能と更新プログラム**です。  
  
     **[拡張機能と更新プログラム]** ダイアログ ボックスが表示されます。  
  
2.  拡張機能の一覧で選択**External Data List Generator**を選択し、**アンインストール**ボタンをクリックします。  
  
3.  表示されるダイアログ ボックスで選択**はい**extension をアンインストールすることを確認します。  
  
4.  選択**今すぐ再起動**してアンインストールを完了します。  
  
5.  Visual Studio の両方のインスタンス (実験用インスタンスと、GenerateExternalDataLists ソリューションを開いたインスタンス) を閉じます。  
  
## <a name="see-also"></a>参照  
 [SharePoint プロジェクト システムの拡張](../sharepoint/extending-the-sharepoint-project-system.md)   
 [ビジネス データ接続モデルを作成します。](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  