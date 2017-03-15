---
title: "従来の言語サービスを移行します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "言語サービスを移行します。"
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# 従来の言語サービスを移行します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

プロジェクトの更新をプロジェクトに source.extension.vsixmanifest ファイルを追加することで、それ以降のバージョンの Visual Studio に従来の言語サービスを移行できます。 言語サービス自体は引き続き機能前回と同様に、Visual Studio エディターで適応させるので。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は、MEF の拡張機能を使用します。 言語サービスを実装する新しい方法の詳細については、次を参照してください。 [エディターと言語サービスの拡張機能](../../extensibility/editor-and-language-service-extensions.md)します。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く始めることをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
## Visual Studio 2008 言語サービス ソリューションを以降のバージョンに移行します。  
 次の手順では、RegExLanguageService という名前の Visual Studio 2008 サンプルを調整する方法を示します。 Visual Studio 2008 SDK のインストールでは、このサンプルを見つけることができます、 *Visual Studio SDK インストール パス*\\VisualStudioIntegration\\Samples\\IDE\\CSharp\\Example.RegExLanguageService\\ フォルダーです。  
  
> [!IMPORTANT]
>  明示的に設定する必要がありますが、言語サービスが色を定義していない場合 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> に `true` VSPackage で。  
  
```  
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]  
```  
  
#### Visual Studio 2008 言語サービスを以降のバージョンに移行するには  
  
1.  新しいバージョンの Visual Studio と Visual Studio SDK をインストールします。 SDK をインストールする方法の詳細については、次を参照してください。 [Visual Studio SDK をインストールします。](../../extensibility/installing-the-visual-studio-sdk.md)します。  
  
2.  \(Visual Studio では、それを読み込んでなし RegExLangServ.csproj ファイルを編集います。  
  
     `Import` Microsoft.VsSDK.targets ファイルを参照するノードは、値を次のテキストに置き換えます。  
  
    ```  
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets  
    ```  
  
3.  ファイルを保存して、閉じます。  
  
4.  RegExLangServ.sln ソリューションを開きます。  
  
5.  **一方向のアップグレード** ウィンドウが表示されます。**\[OK\]** をクリックします。  
  
6.  プロジェクトのプロパティを更新します。 開いている、 **プロジェクトのプロパティの** \] ウィンドウでプロジェクト ノードを選択して、 **ソリューション エクスプ ローラー**, 、右クリックし、選択 **プロパティ**します。  
  
    -   **アプリケーション** \] タブで、変更 **ターゲット フレームワーク** に **4.6.1**します。  
  
    -   **デバッグ** \] タブで、 **外部プログラムの開始** ボックスに、入力 **\< Visual Studio インストール パス \> \\Common7\\IDE\\devenv.exe。**します。  
  
         **コマンドライン引数** ボックスに、入力\/**\/rootsuffix Exp**します。  
  
7.  次の参照を更新します。  
  
    -   Microsoft.VisualStudio.Shell.9.0.dll への参照を削除してから、Microsoft.VisualStudio.Shell.14.0.dll および Microsoft.VisualStudio.Shell.Immutable.11.0.dll への参照を追加します。  
  
    -   Microsoft.VisualStudio.Package.LanguageService.9.0.dll への参照を削除してから、Microsoft.VisualStudio.Package.LanguageService.14.0.dll への参照を追加します。  
  
    -   Microsoft.VisualStudio.Shell.Interop.10.0.dll への参照を追加します。  
  
8.  VsPkg.cs ファイルを開きの値を変更、 `DefaultRegistryRoot` 属性を  
  
    ```  
    "Software\\Microsoft\\VisualStudio\\14.0Exp"  
    ```  
  
9. 元のサンプルでは、VsPkg.cs に次の属性を追加する必要がありますので、その言語サービスは登録されません。  
  
    ```  
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]  
    ```  
  
10. Source.extension.vsixmanifest ファイルを追加する必要があります。  
  
    -   このファイルを既存の拡張機能から、プロジェクト ディレクトリにコピーします。 \(このファイルを取得する方法の 1 つは、VSIX プロジェクトを作成する \(\[ **ファイル**, 、\] をクリックして **新規**, 、\] をクリックし、 **プロジェクト**します。 \[Visual Basic または c\# のクリック **拡張**, 選択してから、 **VSIX プロジェクト**.\)  
  
    -   ファイルをプロジェクトに追加します。  
  
    -   ファイルの **プロパティ**, 、 **ビルド アクション** に **なし**します。  
  
    -   使用してファイルを開き、 **VSIX マニフェスト エディター**します。  
  
    -   次のフィールドを変更します。  
  
    -   **ID**: RegExLangServ  
  
    -   **製品名**: RegExLangServ  
  
    -   **説明**: 正規表現言語サービスです。  
  
    -   \[ **資産**, 、\] をクリックして **新規**, を選択、 **型** に **として \[Microsoft.VisualStudio.VsPackage**, 、設定、 **ソース** に **現在のソリューション内のプロジェクト**, 、し、設定、 **プロジェクト** に **RegExLangServ**します。  
  
    -   ファイルを保存して閉じます。  
  
11. ソリューションをビルドします。 作成済みのファイルが展開されている **%USERPROFILE%\\AppData\\Local\\Microsoft\\VisualStudio\\14.0Exp\\Extensions\\MSIT\\ RegExLangServ\\**します。  
  
12. デバッグを開始します。 Visual Studio の 2 つ目のインスタンスが開かれます。  
  
## 参照  
 [従来の言語サービスの拡張機能](../../extensibility/internals/legacy-language-service-extensibility.md)