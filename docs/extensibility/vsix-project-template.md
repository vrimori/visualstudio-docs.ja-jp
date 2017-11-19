---
title: "VSIX プロジェクト テンプレート |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 24a2937b37aa339f85e197f6ff2bb49cbb0ce86f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="vsix-project-template"></a>VSIX プロジェクト テンプレート
VSIX プロジェクトは、1 つまたは複数の Visual Studio 拡張機能をラップする VSIX プロジェクト テンプレートを使用して上でパッケージを発行、 [Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkID=123847) Web サイトです。  
  
 VSIX 配置には、Vspackage、アセンブリ、MEF コンポーネント、プロジェクト テンプレート、項目テンプレート、ツールボックス コントロール、およびカスタム拡張機能の種類がサポートしています。  
  
> [!NOTE]
>  VSIX プロジェクトを使用するのには、Visual Studio SDK をインストールする必要があります。 Visual Studio SDK の詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)です。  
  
## <a name="where-to-find-the-vsix-project-template"></a>VSIX プロジェクト テンプレートを検索する場所  
 VSIX プロジェクト テンプレートでは使用、**新しいプロジェクト** ダイアログ ボックス。 いずれかを展開、 **Visual Basic**ノードまたは**Visual c#**  ノードを選択し**Extensibility**です。  
  
> [!TIP]
>  確認してください、.NET Framework 4.5 または以降の上部にあるドロップダウン リストで指定する、**新しいプロジェクト** ダイアログ ボックス。  
  
## <a name="uses-of-the-vsix-project-template"></a>VSIX プロジェクト テンプレートの使用  
 VSIX プロジェクト テンプレートには、次の 2 つの主な用途があります。  
  
-   プロジェクト テンプレート、項目テンプレート、および VSIX サポートしていないその他の拡張を展開します。  
  
-   1 つの展開パッケージに複数の拡張機能の出力をラップします。  
  
 VSIX プロジェクト テンプレートを使用して、Vspackage または他の種類が既にあるサポート VSIX 拡張機能の配置する必要はありません。  
  
## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>空の VSIX プロジェクトの拡張機能をパッケージ化  
 既存の拡張機能、または拡張機能をサポートして、空の VSIX プロジェクトにラップする VSIX にまだないをパッケージ化することができます。 サポートされている型の拡張をラップする必要があります、 [VSIX スキーマ](../extensibility/vsix-extension-schema-2-0-reference.md)です。  
  
#### <a name="to-package-an-extension-by-using-a-vsix-project"></a>VSIX プロジェクトを使用して拡張機能をパッケージ化するには  
  
1.  拡張機能を構成するプロジェクトをビルドします。  
  
2.  使用して、VSIX プロジェクトを作成、 **VSIX プロジェクト**テンプレート。  
  
     が開きます Source.extension.vsixmanifest**マニフェスト デザイナー**です。  
  
3.  **資産** タブで、選択、**新規**ボタンをクリックします。  
  
     **新しいアセットの追加** ダイアログ ボックスが表示されます。  
  
4.  **型**リストを追加する拡張機能の種類を選択します。  
  
5.  (項目テンプレートやコンパイル済みアセンブリなど) は、現在のソリューションに含まれている拡張機能またはコンテンツ要素を追加するには、次の手順を実行します。  
  
    1.  **ソース**一覧で、選択**現在のソリューション内のプロジェクト**です。  
  
    2.  **プロジェクト**一覧で、拡張機能の名前を選択します。  
  
    3.  **このフォルダーに埋め込み**ボックスで、資産を埋め込むし、順に選択するためのフォルダーの名前を入力、 **OK**ボタンをクリックします。  
  
6.  拡張機能または現在のソリューションに含まれていないコンテンツの要素を追加するには、次の手順を実行します。  
  
    1.  **ソース**ボックスの一覧で、選択**ファイルシステム上のファイル**です。  
  
    2.  **パス**フィールド拡張子コンパイルまたは圧縮されたファイルを完全なパスを入力するかを使用して、**参照**ファイルを参照するボタンをクリックします。  
  
    3.  **このフォルダーに埋め込み**ボックスで、資産を埋め込むし、順に選択するためのフォルダーの名前を入力、 **OK**ボタンをクリックします。  
  
7.  パッケージに追加の拡張機能を含める場合は、同じ方法で追加します。  
  
8.  ソリューションをビルドします。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSIX マニフェスト ファイル、[Content_Types] .xml ファイル、およびそのすべてのプロジェクトに追加した拡張機能の資産を含む .vsix ファイルを構築します。  
  
## <a name="see-also"></a>関連項目  
 [VSIX 拡張機能スキーマ 2.0 リファレンス](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Visual Studio 拡張機能の検索と使用](../ide/finding-and-using-visual-studio-extensions.md)