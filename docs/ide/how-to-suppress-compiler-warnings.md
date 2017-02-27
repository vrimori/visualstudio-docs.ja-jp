---
title: "方法: コンパイラ警告を非表示にする | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 31827b17-f933-413d-b28a-b19f903b64ca
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# 方法: コンパイラ警告を非表示にする
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

、含めるには、一つ以上の種類のコンパイラの警告を指定して declutter ビルド ログできます。  たとえば、一部と通常、詳細なセットへのビルド ログの詳細度、または診断自動的に生成する情報をすべて確認してこの方法を使用する場合もありますが。  詳細出力に関する詳細については、[方法: ビルド ログ ファイルを表示、保存、および構成する](../ide/how-to-view-save-and-configure-build-log-files.md)を参照してください。  
  
### Visual C\#、F\# の特定の警告を抑制するには  
  
1.  **\[ソリューション エクスプローラー\]** で、警告を抑制するプロジェクトを選択します。  
  
2.  メニュー バーで、**\[ビュー\]**、**\[プロパティ ページ\]** を選択します。  
  
3.  **\[ビルド\]** のページを選択します。  
  
4.  **\[警告の表示なし\]** ボックスに、セミコロンで区切って、非表示にする警告のエラー コードを指定し、ソリューションをビルドし直します。  
  
### Visual C\+\+ の特定の警告を抑制するには  
  
1.  **\[ソリューション エクスプローラー\]** で、警告を抑制するソース ファイルまたはプロジェクトを選択します。  
  
2.  メニュー バーで、**\[ビュー\]**、**\[プロパティ ページ\]** を選択します。  
  
3.  **\[構成プロパティ\]** のカテゴリを選択し、**\[C\/C\+\+\]** のカテゴリを選択し、を **\[詳細\]** のページを選択します。  
  
4.  次のいずれかの操作を実行します。  
  
    -   **\[指定の警告を無効にする\]** ボックスに、セミコロンで区切って、非表示にする警告のエラー コードを指定します。  
  
    -   **\[指定の警告を無効にする\]** ボックスで、追加のオプションを表示するには **\[編集\]** を選択します。  
  
5.  **\[OK\]** のボタンを選択し、ソリューションをビルドし直します。  
  
## Visual Basic の警告の抑制  
 プロジェクトの .vbproj ファイルを編集して Visual Basic の特定のコンパイラの警告を非表示にできます。  また、カテゴリ別に警告を抑制するには [&#91;Compile Page, Project Designer&#93;](../ide/reference/compile-page-project-designer-visual-basic.md) を使用できます。  詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
#### Visual Basic の特定の警告を抑制するには  
  
1.  **\[ソリューション エクスプローラー\]** で、警告を抑制するプロジェクトを選択します。  
  
2.  メニュー バーで、**プロジェクト**、**\[プロジェクトのアンロード\]** を選択します。  
  
3.  **\[ソリューション エクスプローラー\]** では、プロジェクトのショートカット メニューを開き、**\[編集\]***\[プロジェクト名\]***.vbproj**を選択します。  
  
     プロジェクト ファイルがコード エディターで開きます。  
  
4.  ビルドのビルド構成 `<NoWarn></NoWarn>` の要素を見つけます。  
  
     次の例では、x86 プラットフォームのデバッグ ビルド構成を太字テキストで `<NoWarn></NoWarn>` の要素を示しています:  
  
    ```  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">  
        <PlatformTarget>x86</PlatformTarget>  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <ErrorReport>prompt</ErrorReport>  
        <NoWarn> </NoWarn>  
        <WarningLevel>1</WarningLevel>  
      </PropertyGroup>  
    ```  
  
5.  `<NoWarn>` の要素の値として一つ以上の警告番号を追加します。  複数の警告番号を指定した場合は、次の例に示すように、コンマで区切ります。  
  
    ```  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">  
        <PlatformTarget>x86</PlatformTarget>  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <ErrorReport>prompt</ErrorReport>  
        <NoWarn>40059,42024</NoWarn>  
        <WarningLevel>1</WarningLevel>  
      </PropertyGroup>  
    ```  
  
6.  .vbproj ファイルへの変更を保存します。  
  
7.  メニュー バーで、**プロジェクト**、**\[プロジェクトの再読み込み\]** を選択します。  
  
8.  メニュー バーで、**\[ビルド\]**、**\[ソリューションのリビルド\]** を選択します。  
  
     **\[出力\]** のウィンドウは、指定したことを示す警告に表示されません。  
  
 詳細については、「[\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)」を参照してください。  
  
## 参照  
 [チュートリアル: アプリケーションをビルドする](../ide/walkthrough-building-an-application.md)   
 [方法: ビルド ログ ファイルを表示、保存、および構成する](../ide/how-to-view-save-and-configure-build-log-files.md)   
 [Visual Studio でのアプリケーションのビルド](../ide/compiling-and-building-in-visual-studio.md)