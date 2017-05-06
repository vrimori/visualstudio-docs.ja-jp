---
title: "方法: MSBuild ターゲットを使用して SharePoint ソリューション パッケージをカスタマイズする"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio での SharePoint 開発, パッケージ"
ms.assetid: 7fa6a276-04c8-463e-be95-57c2c6240d76
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 方法: MSBuild ターゲットを使用して SharePoint ソリューション パッケージをカスタマイズする
  コマンド プロンプトで MSBuild ターゲットを使用して、Visual Studio が SharePoint パッケージ ファイル \(.wsp\) を作成する方法をカスタマイズできます。  たとえば、パッケージ化の中間ディレクトリと MSBuild 項目グループを変更するために列挙するファイルを指定する MSBuild のプロパティをカスタマイズできます。  
  
## MSBuild ターゲットのカスタマイズと実行  
 BeforeLayout と AfterLayout ターゲットをカスタマイズした場合は、追加、削除、または変更パッケージ化ファイルなどのパッケージのレイアウトの前にタスクを実行できます。  
  
#### BeforeLayout ターゲットをカスタマイズするには  
  
1.  エディターは、メモ帳など\) を開き、次のコードを追加します。  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <Target Name="BeforeLayout">  
        <Message Importance="high" Text="In the BeforeLayout Target"></Message>  
      </Target>  
    </Project>  
    ```  
  
     この例では、このターゲットにパッケージ化する前にメッセージが表示されます。  
  
2.  ファイル **CustomLayout.SharePoint.targets**という名前を付け、SharePoint プロジェクトのフォルダーに保存します。  
  
3.  プロジェクトを開き、ショートカット メニューを開き、**\[プロジェクトのアンロード\]** をクリックします。  
  
4.  **\[ソリューション エクスプローラー\]** で、プロジェクトのショートカット メニューを開き、*ProjectName***\[.vbproj\]** または **\[編集\]***ProjectName***\[.csproj\]** を **\[編集\]** をクリックします。  
  
5.  プロジェクト ファイルの末尾付近に `Import` の行に、次の行を追加した後。  
  
    ```  
    <Import Project="CustomLayout.SharePoint.targets" />  
    ```  
  
6.  プロジェクト ファイルを保存して閉じます。  
  
7.  **\[ソリューション エクスプローラー\]** で、プロジェクトのショートカット メニューを開き、**\[プロジェクトの再読み込み\]** をクリックします。  
  
 プロジェクトを発行する場合、メッセージは出力にパッケージ化する前から表示されます。  
  
#### AfterLayout ターゲットをカスタマイズするには  
  
1.  メニュー バーで、**\[開く\]**、**\[ファイル\]\[ファイル\]** をクリックします。  
  
2.  **\[ファイルを開く\]** ダイアログ ボックスで、プロジェクト フォルダーに移動し、CustomLayout.target ファイルを選択し、**\[開く\]** ボタンをクリックします。  
  
3.  `</Project>` タグは、次のコードを追加するには:  
  
    ```  
    <Target Name="AfterLayout">  
      <Message Importance="high" Text="In the AfterLayout Target"></Message>  
    </Target>  
    ```  
  
     この例ではこのターゲットをパッケージ化とメッセージを表示します。  
  
4.  ターゲット ファイルを保存して閉じます。  
  
5.  Visual Studio を再起動し、プロジェクトを開きます。  
  
 プロジェクトを発行すると、BeforeLayout メッセージは開始をパッケージ化する前に置かれ、AfterLayout メッセージは完了のパッケージ化が完了後に表示されます。  
  
## 参照  
 [SharePoint ソリューションのパッケージ化と配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  