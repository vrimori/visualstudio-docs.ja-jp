---
title: '方法: Visual スタイルが有効になっている WPF アプリケーションの発行 |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fdb508a84e9c258463ca2a9f3971cd51d55b402c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53861502"
---
# <a name="how-to-publish-a-wpf-application-with-visual-styles-enabled"></a>方法: Visual スタイルが有効になっている WPF アプリケーションの発行
visual スタイルを使用すると、ユーザーが選択したテーマに基づいてコモン コントロールの外観を変更できます。 既定では、Visual スタイルは、Windows Presentation Foundation (WPF) アプリケーションで有効になっていないため、手動で有効にする必要があります。 ただし、WPF アプリケーションの Visual スタイルを有効にすると、ソリューションの発行によりエラーが発生します。 このトピックでは、このエラーを解決する方法と、Visual スタイルを有効にした WPF アプリケーションを発行するためのプロセスについて説明します。 Visual スタイルの詳細については、次を参照してください。 [Visual スタイルの概要](/windows/desktop/Controls/visual-styles-overview)します。 エラー メッセージの詳細については、次を参照してください。 [ClickOnce 配置で特定のエラーのトラブルシューティング](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)します。  
  
 エラーを解決し、ソリューションを発行するには、次のタスクを実行します。  
  
- [Visual スタイルを有効にせずにソリューションを公開します](#publish-the-solution-without-visual-styles-enabled)。  
  
- [マニフェスト ファイルを作成します](#create-a-manifest-file)。  
  
- [マニフェスト ファイルを発行済みソリューションの実行可能ファイルに埋め込みます](#embed-the-manifest-file-into-the-executable-file-of-the-published-solution)。  
  
- [アプリケーション マニフェストと配置マニフェストに署名します](#sign-the-application-and-deployment-manifests)。  
  
  その後、エンド ユーザーがアプリケーションをインストールする場所に、発行されたファイルを移動できます。  
  
##  <a name="publish-the-solution-without-visual-styles-enabled"></a>Visual スタイルを有効にせずにソリューションを公開するには  
  
1.  プロジェクトに有効になった Visual スタイルがないことを確認します。 最初に、プロジェクトのマニフェスト ファイルに次の XML があるかチェックします。 その後、XML がある場合は、コメント タグで XML を囲みます。  
  
     既定では、Visual スタイルは有効になっていません。  
  
    ```xml  
    <dependency>
        <dependentAssembly>
            <assemblyIdentity type="win32" name="Microsoft.Windows.Common-Controls" version="6.0.0.0" processorArchitecture="*" publicKeyToken="6595b64144ccf1df" language="*" />
        </dependentAssembly>
    </dependency>
    ```  
  
     次の手順は、プロジェクトに関連付けられたマニフェスト ファイルを開く方法を示します。  
  
    ###### <a name="to-open-the-manifest-file-in-a-visual-basic-project"></a>Visual Basic プロジェクトのマニフェスト ファイルを開くには  
  
    1.  メニュー バーで、**プロジェクト**、 *ProjectName* **プロパティ**ここで、 *ProjectName* WPF プロジェクトの名前を指定します。  
  
         WPF プロジェクトのプロパティ ページが表示されます。  
  
    2.  **[アプリケーション]** タブで、**[Windows 設定の表示]** をクリックします。  
  
         **コード エディター**で app.manifest ファイルが開きます。  
  
    ###### <a name="to-open-the-manifest-file-in-a-c-project"></a>C# プロジェクトのマニフェスト ファイルを開くには  
  
    1.  メニュー バーで、**プロジェクト**、 *ProjectName* **プロパティ**ここで、 *ProjectName* WPF プロジェクトの名前を指定します。  
  
         WPF プロジェクトのプロパティ ページが表示されます。  
  
    2.  **[アプリケーション]** タブで、マニフェストのフィールドに表示される名前をメモします。 これは、プロジェクトに関連付けられているマニフェストの名前です。  
  
        > [!NOTE]
        >  **[マニフェストを既定の設定で埋め込みます]** または **[マニフェストなしでアプリケーションを作成する]** がマニフェスト フィールドに表示されている場合、Visual スタイルは有効になりません。 マニフェスト ファイルの名前がマニフェスト フィールドに表示されている場合は、この手順の次の手順に進みます。  
  
    3.  **ソリューション エクスプローラー**で、**[すべてのファイルを表示]** をクリックします。  
  
         このボタンは、除外された項目や通常は表示されない項目も含め、すべてのプロジェクト項目を表示します。 マニフェスト ファイルはプロジェクト項目として表示されます。  
  
2.  ソリューションをビルドし、発行します。 ソリューションを発行する方法の詳細については、次を参照してください。[方法。発行ウィザードを使用して ClickOnce アプリケーションを発行する](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)  
  
## <a name="create-a-manifest-file"></a>マニフェスト ファイルの作成  
  
1.  次の XML をメモ帳ファイルに貼り付けます。  
  
     この XML は、Visual スタイルをサポートするコントロールを含むアセンブリについて説明します。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>
    <asmv1:assembly manifestVersion="1.0" 
        xmlns="urn:schemas-microsoft-com:asm.v1" 
        xmlns:asmv1="urn:schemas-microsoft-com:asm.v1" 
        xmlns:asmv2="urn:schemas-microsoft-com:asm.v2" 
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
        <dependency>
            <dependentAssembly>
                <assemblyIdentity type="win32" name="Microsoft.Windows.Common-Controls" version="6.0.0.0" processorArchitecture="*" publicKeyToken="6595b64144ccf1df" language="*" />
            </dependentAssembly>
        </dependency>
    </asmv1:assembly>
    ```  
  
2.  メモ帳の **[ファイル]** をクリックし、**[名前を付けて保存]** をクリックします。  
  
3.  **[名前を付けて保存]** ダイアログ ボックスの **[ファイルの種類]** ドロップダウン リストで、**[すべてのファイル]** をクリックします。  
  
4.  **[ファイル名]** ボックスで、ファイルに名前を付け、ファイル名の最後に *.manifest* を付けます。 例: *themes.manifest*。  
  
5.  **[フォルダーの参照]** ボタンをクリックしてフォルダーを選択し、**[保存]** をクリックします。  
  
    > [!NOTE]
    >  残りの手順では、このファイルの名前が *themes.manifest* で、ファイルがコンピューターの *C:\temp* ディレクトリに格納されていることを前提とします。  
  
## <a name="embed-the-manifest-file-into-the-executable-file-of-the-published-solution"></a>マニフェスト ファイルを発行済みソリューションの実行可能ファイルに埋め込むには  
  
1. **Visual Studio コマンド プロンプト**を開きます。  
  
    詳細を開く方法については、 **Visual Studio コマンド プロンプト**を参照してください[コマンド プロンプト](/dotnet/framework/tools/developer-command-prompt-for-vs)します。  
  
   > [!NOTE]
   >  残りの手順は、ソリューションに関して以下を前提とします。  
   > 
   > - ソリューションの名前は **MyWPFProject** です。  
   >   -   ソリューションは、次のディレクトリにある:`%UserProfile%\Documents\Visual Studio 2010\Projects\`します。  
   > 
   >   次のディレクトリにソリューションを発行:`%UserProfile%\Documents\Visual Studio 2010\Projects\publish`します。  
   >   -   発行済みアプリケーション ファイルの最新バージョンについては、次のディレクトリにあります。 `%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`  
   > 
   >   上記の名前とディレクトリの場所は、いずれも使用する必要はありません。 前の名前と場所は、ソリューションの公開に必要な手順について説明するためにのみ使用されます。  
  
2. コマンド プロンプトで、発行済みのアプリケーション ファイルの最新バージョンが含まれるディレクトリへのパスを変更します。 この手順を次の例に示します。  
  
   ```cmd  
   cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"  
   ```  
  
3. コマンド プロンプトで、次のコマンドを実行して、アプリケーションの実行可能ファイルにマニフェスト ファイルを埋め込みます。  
  
   ```cmd
   mt -manifest c:\temp\themes.manifest -outputresource:MyWPFApp.exe.deploy  
   ```  
  
## <a name="sign-the-application-and-deployment-manifests"></a>アプリケーション マニフェストと配置マニフェストに署名します。  
  
1. コマンド プロンプトでは、削除するには、次のコマンドを実行、 *.deploy*現在のディレクトリで実行可能ファイルから拡張機能。  
  
   ```cmd  
   ren MyWPFApp.exe.deploy MyWPFApp.exe  
   ```  
  
   > [!NOTE]
   >  この例では、1 ファイルだけが、 *.deploy*ファイル拡張子。 このディレクトリを持つすべてのファイルの名前を変更することを確認、 *.deploy*ファイル拡張子。  
  
2. コマンド プロンプトで、次のコマンドを実行してアプリケーション マニフェストに署名します。  
  
   ```cmd  
   mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
   ```  
  
   > [!NOTE]
   >  この例を使用して、マニフェストに署名すること、 *.pfx*プロジェクトのファイル。 マニフェストに署名していない場合は、省略、`-cf`この例で使用されるパラメーター。 パスワードが必要な証明書でマニフェストに署名する場合の指定、`-password`オプション (`For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password`)。  
  
3. コマンド プロンプトでは、追加するには、次のコマンドを実行、 *.deploy*拡張機能には、この手順の前の手順で名前を変更したファイルの名前。  
  
   ```  
   ren MyWPFApp.exe MyWPFApp.exe.deploy  
   ```  
  
   > [!NOTE]
   >  この例では 1 ファイルだけが、 *.deploy*ファイル拡張子。 以前にこのディレクトリ内のすべてのファイルの名前を変更することを確認、 *.deploy*ファイル名拡張子。  
  
4. コマンド プロンプトで、次のコマンドを実行して配置マニフェストに署名します。  
  
   ```  
   mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
   ```  
  
   > [!NOTE]
   >  この例を使用して、マニフェストに署名すること、 *.pfx*プロジェクトのファイル。 マニフェストに署名していない場合は、省略、`-cf`この例で使用されるパラメーター。 パスワードが必要な証明書でマニフェストに署名する場合の指定、`-password`オプションは、この例のように:`For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password`します。  
  
   これらの手順を実行した後、エンド ユーザーがアプリケーションをインストールする場所に、発行されたファイルを移動できます。 ソリューションを頻繁に更新する場合は、新しいバージョンを発行するたびに、スクリプトにこれらのコマンドを移動し、スクリプトを実行できます。  
  
## <a name="see-also"></a>関連項目

-[ClickOnce 配置の固有のエラーのトラブルシューティング](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)
- [Visual スタイルの概要](/windows/desktop/Controls/visual-styles-overview)
- [視覚スタイルを有効にする](/windows/desktop/Controls/cookbook-overview)
- [Visual Studio 用開発者コマンド プロンプト](/dotnet/framework/tools/developer-command-prompt-for-vs)
