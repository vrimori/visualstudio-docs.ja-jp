---
title: '方法: Visual スタイルが有効になっている WPF アプリケーションの発行 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: f03dc4ea85fe0f44ea2253da9544ace9b0068abc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922472"
---
# <a name="how-to-publish-a-wpf-application-with-visual-styles-enabled"></a>方法: Visual スタイルが有効になっている WPF アプリケーションを公開する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

visual スタイルを使用すると、ユーザーが選択したテーマに基づいてコモン コントロールの外観を変更できます。 既定では、Visual スタイルは、Windows Presentation Foundation (WPF) アプリケーションで有効になっていないため、手動で有効にする必要があります。 ただし、WPF アプリケーションの Visual スタイルを有効にすると、ソリューションの発行によりエラーが発生します。 このトピックでは、このエラーを解決する方法と、Visual スタイルを有効にした WPF アプリケーションを発行するためのプロセスについて説明します。 Visual スタイルの詳細については、次を参照してください。 [Visual スタイルの概要](http://msdn.microsoft.com/en-us/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e)します。 エラー メッセージの詳細については、次を参照してください。 [ClickOnce 配置での特定のエラーをトラブルシューティング](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)します。  
  
 エラーを解決し、ソリューションを発行するには、次のタスクを実行します。  
  
- [Visual スタイルを有効にせずに、ソリューションを発行](#BKMK_publishsolwovs)します。  
  
- [マニフェスト ファイルを作成](#BKMK_CreateManifest)です。  
  
- [発行済みのソリューションの実行可能ファイルにマニフェスト ファイルを埋め込む](#BKMK_embedmanifest)します。  
  
- [アプリケーションと配置マニフェストに署名](#BKMK_signappdeplyman)します。  
  
  その後、エンド ユーザーがアプリケーションをインストールする場所に、発行されたファイルを移動できます。  
  
##  <a name="BKMK_publishsolwovs"></a> Visual スタイルを有効にせずに、ソリューションを発行します。  
  
1.  プロジェクトに有効になった Visual スタイルがないことを確認します。 最初に、プロジェクトのマニフェスト ファイルに次の XML があるかチェックします。 その後、XML がある場合は、コメント タグで XML を囲みます。  
  
     既定では、Visual スタイルは有効になっていません。  
  
    ```  
    <dependency>    <dependentAssembly>      <assemblyIdentity          type="win32"          name="Microsoft.Windows.Common-Controls"          version="6.0.0.0"          processorArchitecture="*"          publicKeyToken="6595b64144ccf1df"          language="*"        />    </dependentAssembly>  </dependency>  
    ```  
  
     次の手順は、プロジェクトに関連付けられたマニフェスト ファイルを開く方法を示します。  
  
    ###### <a name="to-open-the-manifest-file-in-a-visual-basic-project"></a>Visual Basic プロジェクトのマニフェスト ファイルを開くには  
  
    1.  メニュー バーで、**プロジェクト**、 _ProjectName_**プロパティ**ここで、 *ProjectName* WPF プロジェクトの名前を指定します。  
  
         WPF プロジェクトのプロパティ ページが表示されます。  
  
    2.  **アプリケーション** タブで、選択**Windows 設定の表示**します。  
  
         App.manifest ファイルが開きます、**コード エディター**します。  
  
    ###### <a name="to-open-the-manifest-file-in-a-c-project"></a>C# プロジェクトのマニフェスト ファイルを開くには  
  
    1.  メニュー バーで、**プロジェクト**、 _ProjectName_**プロパティ**ここで、 *ProjectName* WPF プロジェクトの名前を指定します。  
  
         WPF プロジェクトのプロパティ ページが表示されます。  
  
    2.  **アプリケーション** タブで、マニフェスト フィールドに表示される名前をメモしておきます。 これは、プロジェクトに関連付けられているマニフェストの名前です。  
  
        > [!NOTE]
        >  場合**既定の設定を使用して埋め込みマニフェスト**または**マニフェストなしにアプリケーション作成**visual スタイルが有効になっていないマニフェストのフィールドに表示されます。 マニフェスト ファイルの名前がマニフェスト フィールドに表示されている場合は、この手順の次の手順に進みます。  
  
    3.  **ソリューション エクスプ ローラー**、選択**すべてのファイル**()。  
  
         このボタンは、除外された項目や通常は表示されない項目も含め、すべてのプロジェクト項目を表示します。 マニフェスト ファイルはプロジェクト項目として表示されます。  
  
2.  ソリューションをビルドし、発行します。 ソリューションを発行する方法の詳細については、次を参照してください。[方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)します。  
  
##  <a name="BKMK_CreateManifest"></a> マニフェスト ファイルを作成します。  
  
1.  次の XML をメモ帳ファイルに貼り付けます。  
  
     この XML は、Visual スタイルをサポートするコントロールを含むアセンブリについて説明します。  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?><asmv1:assembly manifestVersion="1.0"                xmlns="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"                xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  <dependency>    <dependentAssembly>      <assemblyIdentity        type="win32"        name="Microsoft.Windows.Common-Controls"        version="6.0.0.0"        processorArchitecture="*"        publicKeyToken="6595b64144ccf1df"        language="*"        />    </dependentAssembly>  </dependency></asmv1:assembly>  
    ```  
  
2.  メモ帳で、**ファイル**、 をクリックし、**名前を付けて保存**します。  
  
3.  **名前を付けて保存** ダイアログ ボックスで、**型として保存**ドロップダウン リストで、**すべてのファイル**します。  
  
4.  **ファイル名**ボックス、ファイルの名前し、追加 **.manifest**ファイル名の末尾にします。 例: **themes.manifest**します。  
  
5.  選択、**フォルダーの参照**ボタンをクリックし、任意のフォルダーを選択し、クリックして**保存**します。  
  
    > [!NOTE]
    >  残りの手順では、このファイルの名前があると仮定**themes.manifest**ファイルは、コンピューターの C:\temp ディレクトリに保存されているとします。  
  
##  <a name="BKMK_embedmanifest"></a> 発行済みのソリューションの実行可能ファイルにマニフェスト ファイルを埋め込む  
  
1. 開く、 **Visual Studio コマンド プロンプト**します。  
  
    詳細を開く方法については、 **Visual Studio コマンド プロンプト**を参照してください[コマンド プロンプト](http://msdn.microsoft.com/library/94fcf524-9045-4993-bfb2-e2d8bad44219)します。  
  
   > [!NOTE]
   >  残りの手順は、ソリューションに関して以下を前提とします。  
   > 
   > - ソリューションの名前は**mywpfproject です**します。  
   >   -   ソリューションは、次のディレクトリにある:`%UserProfile%\Documents\Visual Studio 2010\Projects\`します。  
   > 
   >   次のディレクトリにソリューションを発行:`%UserProfile%\Documents\Visual Studio 2010\Projects\publish`します。  
   >   -   発行済みアプリケーション ファイルの最新バージョンについては、次のディレクトリにあります。 `%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`  
   > 
   >   上記の名前とディレクトリの場所は、いずれも使用する必要はありません。 前の名前と場所は、ソリューションの公開に必要な手順について説明するためにのみ使用されます。  
  
2. コマンド プロンプトで、発行済みのアプリケーション ファイルの最新バージョンが含まれるディレクトリへのパスを変更します。 この手順を次の例に示します。  
  
   ```  
   cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"  
   ```  
  
3. コマンド プロンプトで、次のコマンドを実行して、アプリケーションの実行可能ファイルにマニフェスト ファイルを埋め込みます。  
  
   ```  
   mt –manifest c:\temp\themes.manifest –outputresource:MyWPFApp.exe.deploy  
   ```  
  
##  <a name="BKMK_signappdeplyman"></a> アプリケーションと配置マニフェストに署名します。  
  
1. コマンド プロンプトで、次のコマンドを実行して、現在のディレクトリ内の実行可能ファイルから `.deploy` 拡張子を削除します。  
  
   ```  
   ren MyWPFApp.exe.deploy MyWPFApp.exe  
   ```  
  
   > [!NOTE]
   >  この例では、1 つのファイルだけが `.deploy` ファイル拡張子を持っていると仮定しています。 このディレクトリ内の `.deploy` 拡張子を持つすべてのファイルの名前を変更してください。  
  
2. コマンド プロンプトで、次のコマンドを実行してアプリケーション マニフェストに署名します。  
  
   ```  
   mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
   ```  
  
   > [!NOTE]
   >  この例では、プロジェクトの `.pfx` ファイルを使用してマニフェストに署名すると仮定しています。 マニフェストに署名していない場合は、省略、`–cf`この例で使用されるパラメーター。 パスワードが必要な証明書でマニフェストに署名する場合の指定、`–password`オプション (`For example: mage –u MyWPFApp.exe.manifest –cf ..\..\..\MyWPFApp_TemporaryKey.pfx – password Password`)。  
  
3. コマンド プロンプトで、次のコマンドを実行して、この手順の前の手順で名前を変更したファイルの名前に `.deploy` 拡張子を追加します。  
  
   ```  
   ren MyWPFApp.exe MyWPFApp.exe.deploy  
   ```  
  
   > [!NOTE]
   >  この例では、1 つのファイルだけが `.deploy` ファイル拡張子を持っていたと仮定しています。 このディレクトリ内の `.deploy` 拡張子を持っていたすべてのファイルの名前を変更してください。  
  
4. コマンド プロンプトで、次のコマンドを実行して配置マニフェストに署名します。  
  
   ```  
   mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
   ```  
  
   > [!NOTE]
   >  この例では、プロジェクトの `.pfx` ファイルを使用してマニフェストに署名すると仮定しています。 マニフェストに署名していない場合は、省略、`–cf`この例で使用されるパラメーター。 パスワードが必要な証明書でマニフェストに署名する場合の指定、`–password`オプションは、この例のように:`For example: mage –u MyWPFApp.exe.manifest –cf ..\..\..\MyWPFApp_TemporaryKey.pfx – password Password`します。  
  
   これらの手順を実行した後、エンド ユーザーがアプリケーションをインストールする場所に、発行されたファイルを移動できます。 ソリューションを頻繁に更新する場合は、新しいバージョンを発行するたびに、スクリプトにこれらのコマンドを移動し、スクリプトを実行できます。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce 配置で特定のエラーのトラブルシューティング](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)   
 [Visual スタイルの概要](http://msdn.microsoft.com/en-us/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e)   
 [Visual Studio 用開発者コマンド プロンプト](http://msdn.microsoft.com/library/94fcf524-9045-4993-bfb2-e2d8bad44219)



