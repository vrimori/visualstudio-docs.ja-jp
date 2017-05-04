---
title: "方法: MSBuild タスクを使用して SharePoint ソリューション パッケージを作成する | Microsoft Docs"
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
ms.assetid: c3880bdd-f0a1-4d53-9a97-5767cb3f7b8e
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# 方法: MSBuild タスクを使用して SharePoint ソリューション パッケージを作成する
  開発コンピューターからコマンドラインで MSBuild タスクを使用することによって、SharePoint パッケージ \(.wsp\) のビルド、クリーン、および検証を行うことができます。  これらのコマンドを使用して、ビルド コンピューター上の Team Foundation Server によるビルド処理の自動化も行うことができます。  
  
## SharePoint パッケージのビルド  
  
#### SharePoint パッケージをビルドするには  
  
1.  Windows の **\[開始\]** メニューで、**\[アクセサリ\]**、**\[コマンド プロンプト\]\[すべてのプログラム\]** をクリックします。  
  
2.  SharePoint プロジェクトが存在するディレクトリに変更します。  
  
3.  プロジェクトのパッケージを作成するには、次のコマンドを入力します。  プロジェクトの名前と *ProjectFileName* を置き換えます。  
  
    ```  
    msbuild /t:Package ProjectFileName  
    ```  
  
     たとえば、ListDefinition1 という SharePoint プロジェクトをパッケージ化するには、次のいずれかのコマンドを実行します。  
  
    ```  
    msbuild /t:Package ListDefinition1.vbproj  
    msbuild /t:Package ListDefinition1.csproj  
    ```  
  
## SharePoint パッケージのクリーン  
  
#### SharePoint パッケージをクリーンするには  
  
1.  コマンド プロンプト ウィンドウを開きます。  
  
2.  SharePoint プロジェクトが存在するディレクトリに変更します。  
  
3.  プロジェクトのパッケージをクリーンするには、次のコマンドを入力します。  プロジェクトの名前と *ProjectFileName* を置き換えます。  
  
    ```  
    msbuild /t:CleanPackage ProjectFileName  
    ```  
  
     たとえば、ListDefinition1 という SharePoint プロジェクトをクリーンするには、次のいずれかのコマンドを実行します。  
  
    ```  
    msbuild /t:CleanPackage ListDefinition1.vbproj  
    msbuild /t:CleanPackage ListDefinition1.csproj  
    ```  
  
## SharePoint パッケージの検証  
  
#### SharePoint パッケージを検証するには  
  
1.  コマンド プロンプト ウィンドウを開きます。  
  
2.  SharePoint プロジェクトが存在するディレクトリに変更します。  
  
3.  プロジェクトのパッケージを検証するには、次のコマンドを入力します。  プロジェクトの名前と *ProjectFileName* を置き換えます。  
  
    ```  
    msbuild /t:ValidatePackage ProjectFileName  
    ```  
  
     たとえば、ListDefinition1 という SharePoint プロジェクトを検証するには、次のいずれかのコマンドを実行します。  
  
    ```  
    msbuild /t:ValidatePackage ListDefinition1.vbproj  
    msbuild /t:ValidatePackage ListDefinition1.csproj  
    ```  
  
## SharePoint パッケージのプロパティの設定  
  
#### SharePoint パッケージのプロパティを設定するには  
  
1.  コマンド プロンプト ウィンドウを開きます。  
  
2.  SharePoint プロジェクトが存在するディレクトリに変更します。  
  
3.  プロジェクトのパッケージのプロパティを設定するには、次のコマンドを入力します。  設定するプロパティと *PropertyName* を置き換えます。  
  
    ```  
    msbuild /property:PropertyName=Value  
    ```  
  
     たとえば、警告レベルを設定するには次のコマンドを実行します。  
  
    ```  
    msbuild /property:WarningLevel = 2  
    ```  
  
## 参照  
 [SharePoint フィーチャーの作成](../sharepoint/creating-sharepoint-features.md)   
 [方法: SharePoint フィーチャーをカスタマイズする](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [方法: SharePoint フィーチャーの項目を追加および削除する](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
  