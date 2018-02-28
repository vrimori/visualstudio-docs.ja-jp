---
title: "レガシ言語サービスの移行 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4f5f7cff29dd368acbbc3f599ec0cf623343031f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="migrating-a-legacy-language-service"></a>従来の言語サービスを移行します。
プロジェクトを更新して、source.extension.vsixmanifest ファイルをプロジェクトに追加することによって、以降のバージョンの Visual Studio にレガシ言語サービスを移行できます。 言語サービス自体は引き続き以前と同様、関数、Visual Studio エディターで適応させるのでします。  
  
 レガシ言語サービスは、VSPackage の一部として実装されますが、MEF 拡張機能を使用する言語サービスの機能を実装する新しい方法です。 言語サービスを実装する新しい方法の詳細についてを参照してください。[エディターおよび言語サービス拡張](../../extensibility/editor-and-language-service-extensions.md)です。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>以降のバージョンに、Visual Studio 2008 言語サービス ソリューションを移行します。  
 次の手順では、RegExLanguageService をという名前の Visual Studio 2008 例を改変する方法を示します。 Visual Studio 2008 SDK のインストールでは、このサンプルを見つけることができます、 *Visual Studio SDK インストール パス*\VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\ フォルダーです。  
  
> [!IMPORTANT]
>  明示的に設定する必要がある場合は、言語サービスは、色を定義していない、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A>に`true`を VSPackage に。  
  
```  
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]  
```  
  
#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>以降のバージョンに Visual Studio 2008 言語サービスを移行するには  
  
1.  新しいバージョンの Visual Studio と Visual Studio SDK をインストールします。 SDK をインストールする方法の詳細については、次を参照してください。 [、Visual Studio SDK をインストールする](../../extensibility/installing-the-visual-studio-sdk.md)です。  
  
2.  ファイルを編集して RegExLangServ.csproj (なし、Visual Studio では、それを読み込んでいます。  
  
     `Import` Microsoft.VsSDK.targets ファイルを参照するノードは、値を次のテキストに置き換えます。  
  
    ```  
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets  
    ```  
  
3.  ファイルを保存し、閉じます。  
  
4.  RegExLangServ.sln ソリューションを開きます。  
  
5.  **一方向のアップグレード**ウィンドウが表示されます。 **[OK]**をクリックします。  
  
6.  プロジェクトのプロパティを更新します。 開く、**プロジェクト プロパティ** ウィンドウでプロジェクト ノードを選択して、**ソリューション エクスプ ローラー**、右クリックし、選択**プロパティ**です。  
  
    -   **アプリケーション** タブで、変更**ターゲット フレームワーク**に**4.6.1**です。  
  
    -   **デバッグ** タブで、**外部プログラムの開始**ボックスに、入力 **\<Visual Studio インストール パス > \Common7\IDE\devenv.exe。**です。  
  
         **コマンドライン引数**ボックスに、入力/**/rootsuffix Exp**です。  
  
7.  次の参照を更新します。  
  
    -   Microsoft.VisualStudio.Shell.9.0.dll への参照を削除してから、Microsoft.VisualStudio.Shell.14.0.dll および Microsoft.VisualStudio.Shell.Immutable.11.0.dll への参照を追加します。  
  
    -   Microsoft.VisualStudio.Package.LanguageService.9.0.dll への参照を削除してから、Microsoft.VisualStudio.Package.LanguageService.14.0.dll への参照を追加します。  
  
    -   Microsoft.VisualStudio.Shell.Interop.10.0.dll への参照を追加します。  
  
8.  VsPkg.cs ファイルを開きの値を変更、`DefaultRegistryRoot`属性を  
  
    ```  
    "Software\\Microsoft\\VisualStudio\\14.0Exp"  
    ```  
  
9. VsPkg.cs に次の属性を追加する必要がありますので、元のサンプルは、言語サービスを登録できません。  
  
    ```  
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]  
    ```  
  
10. Source.extension.vsixmanifest ファイルを追加する必要があります。  
  
    -   このファイルを既存の拡張機能から、プロジェクト ディレクトリにコピーします。 (このファイルを取得する方法の 1 つは、VSIX プロジェクトを作成する ([**ファイル**、] をクリックして**新規**、をクリックして**プロジェクト**です。 Visual Basic や c# のクリック**Extensibility**選択してから、 **VSIX プロジェクト**)。  
  
    -   ファイルをプロジェクトに追加します。  
  
    -   ファイルの**プロパティ**設定、**ビルド アクション**に**None**です。  
  
    -   使用してファイルを開き、 **VSIX マニフェスト エディター**です。  
  
    -   次のフィールドを変更します。  
  
    -   **ID**: RegExLangServ  
  
    -   **製品名**: RegExLangServ  
  
    -   **説明**: 正規表現言語サービス。  
  
    -   [**資産**、] をクリックして**新規**を選択、**型**に**Microsoft.VisualStudio.VsPackage**、設定、**ソース**に**現在のソリューション内のプロジェクト**、し、設定、**プロジェクト**に**RegExLangServ**です。  
  
    -   ファイルを保存して閉じます。  
  
11. ソリューションをビルドします。 ビルドされたファイルに配置されます**%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\ RegExLangServ\\**です。  
  
12. デバッグを開始します。 Visual Studio の 2 番目のインスタンスが開かれます。  
  
## <a name="see-also"></a>参照  
 [従来の言語サービスの機能拡張](../../extensibility/internals/legacy-language-service-extensibility.md)