---
title: "VSIX プロジェクト テンプレート | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "パッケージを展開します。"
  - "拡張機能を公開します。"
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# VSIX プロジェクト テンプレート
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSIX プロジェクトの場合は、1 つまたは複数の Visual Studio 拡張機能をラップする VSIX プロジェクト テンプレートを使用してパッケージを公開、 [Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkID=123847) Web サイトです。  
  
 VSIX 配置には、vspackages にある、アセンブリ、MEF コンポーネント、プロジェクト テンプレート、項目テンプレート、ツールボックス コントロール、およびカスタム拡張機能の種類がサポートしています。  
  
> [!NOTE]
>  VSIX プロジェクトを使用するには、Visual Studio SDK をインストールする必要があります。 Visual Studio SDK の詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)します。  
  
## VSIX プロジェクトのテンプレートの入手先  
 VSIX プロジェクト テンプレートでは使用、 **新しいプロジェクト** \] ダイアログ ボックス。 いずれかを展開、 **Visual Basic** ノードまたは **Visual c\#** \] ノードを選択し **拡張**します。  
  
> [!TIP]
>  確認してください、.NET Framework 4.5 または以降の上部にあるドロップダウン リストで指定する、 **新しいプロジェクト** \] ダイアログ ボックス。  
  
## VSIX プロジェクトのテンプレートの使用方法  
 VSIX プロジェクトのテンプレートには、2 つの主な用途があります。  
  
-   プロジェクト テンプレート、項目テンプレート、および VSIX サポートしていない他の拡張機能を展開できます。  
  
-   1 つの展開パッケージに複数の拡張機能の出力をラップします。  
  
 VSIX プロジェクト テンプレートを使用して、VSPackages または他の種類をサポートする VSIX が既に存在する拡張機能の展開する必要はありません。  
  
## 空の VSIX プロジェクトで拡張機能をパッケージ化  
 既存の拡張機能やサポートには、空の VSIX プロジェクトをラップして、VSIX ない拡張機能をパッケージ化することができます。 ラップされる拡張機能でサポートされている型でなければなりません、 [VSIX スキーマ](../extensibility/vsix-extension-schema-2-0-reference.md)します。  
  
#### VSIX プロジェクトを使用して拡張機能をパッケージ化するには  
  
1.  拡張機能を構成するプロジェクトをビルドします。  
  
2.  使用して、VSIX プロジェクトを作成、 **VSIX プロジェクト** テンプレートです。  
  
     Source.extension.vsixmanifest がで開きます **マニフェスト デザイナー**します。  
  
3.  **\[アセット\]** タブで **\[新規作成\]** をクリックします。  
  
     **\[Add New Asset\]** \(新しいアセットの追加\) ダイアログ ボックスが表示されます。  
  
4.  **型** ボックスの一覧で、追加する拡張子の種類を選択します。  
  
5.  現在のソリューション \(たとえば、項目テンプレートまたはコンパイル済みアセンブリ\) に含まれている拡張機能またはコンテンツ要素を追加するには、次の手順を実行します。  
  
    1.  **\[ソース\]** ボックスの一覧で **\[A project in current solution\]** \(現在のソリューション内のプロジェクト\) を選択します。  
  
    2.  **プロジェクト** ボックスの一覧で、拡張機能の名前を選択します。  
  
    3.  **このフォルダーに埋め込む** ボックスで、資産を埋め込むし、順に選択するためのフォルダーの名前を入力、 **OK** \] ボタンをクリックします。  
  
6.  拡張機能または現在のソリューションに含まれないコンテンツの要素を追加するには、次の手順を実行します。  
  
    1.  **ソース** ボックスの一覧で、選択 **ファイルシステム上のファイル**します。  
  
    2.  **パス** フィールドで、拡張子がコンパイルまたは圧縮されたファイルへの完全なパスを入力またはを使用して、 **参照** ファイルを参照するボタンをクリックします。  
  
    3.  **このフォルダーに埋め込む** ボックスで、資産を埋め込むし、順に選択するためのフォルダーの名前を入力、 **OK** \] ボタンをクリックします。  
  
7.  パッケージに追加の拡張機能を含める場合は、同様に、それらを追加します。  
  
8.  ソリューションをビルドします。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX のマニフェスト ファイル、\[Content\_Types\] .xml ファイル、およびそのすべてのプロジェクトに追加する拡張子資産を含む .vsix ファイルを作成します。  
  
## 参照  
 [VSIX 拡張機能スキーマ 2.0 リファレンス](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Visual Studio 拡張機能の検索と使用](../ide/finding-and-using-visual-studio-extensions.md)