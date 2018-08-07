---
title: VSIX プロジェクト テンプレート |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d2309428ffa87409bd35f1a05c2cfd591db3cc1a
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586288"
---
# <a name="vsix-project-template"></a>VSIX プロジェクト テンプレート
VSIX プロジェクトでは、1 つまたは複数の Visual Studio 拡張機能をラップする VSIX プロジェクト テンプレートを使用してでパッケージを公開、 [Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkID=123847) Web サイト。  
  
 VSIX 配置には、Vspackage、アセンブリ、MEF コンポーネント、プロジェクト テンプレート、項目テンプレート、ツールボックス コントロール、およびカスタム拡張機能の種類がサポートしています。  
  
> [!NOTE]
>  VSIX プロジェクトを使用するには、Visual Studio SDK をインストールする必要があります。 Visual Studio SDK の詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)します。  
  
## <a name="where-to-find-the-vsix-project-template"></a>VSIX プロジェクト テンプレートの検索場所  
 VSIX プロジェクト テンプレートが表示されます、**新しいプロジェクト** ダイアログ ボックス。 いずれかを展開、 **Visual Basic**ノードまたは**Visual c#** ノードを選び、**拡張**します。  
  
> [!TIP]
>  以降の上部にあるドロップダウン リスト ボックスで指定されたかを確認してください、.NET Framework 4.5、**新しいプロジェクト** ダイアログ ボックス。  
  
## <a name="uses-of-the-vsix-project-template"></a>VSIX プロジェクト テンプレートの使用  
 VSIX プロジェクト テンプレートでは、2 つの主な用途があります。  
  
-   プロジェクト テンプレートや項目テンプレート、VSIX のサポートがまだない他の拡張機能を展開できます。  
  
-   1 つの展開パッケージに複数の拡張機能の出力をラップします。  
  
 VSIX プロジェクト テンプレートを使用して、Vspackage またはその他の拡張機能をサポートする VSIX が既に存在するデプロイする必要はありません。  
  
## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>空の VSIX プロジェクトの拡張機能をパッケージ化  
 既存の拡張機能、または拡張機能を VSIX に空の VSIX プロジェクトにラップすることによって、サポートがないパッケージ化することができます。 サポートされている型の拡張機能をラップする必要があります、 [VSIX スキーマ](../extensibility/vsix-extension-schema-2-0-reference.md)します。  
  
### <a name="to-package-an-extension-by-using-a-vsix-project"></a>VSIX プロジェクトを使用して拡張機能をパッケージ化するには  
  
1.  拡張機能を構成するプロジェクトをビルドします。  
  
2.  使用して、VSIX プロジェクトを作成、 **VSIX プロジェクト**テンプレート。  
  
     *Source.extension.vsixmanifest*で開きます**マニフェスト デザイナー**します。  
  
3.  **資産** タブで、選択、**新規**ボタンをクリックします。  
  
     **新しい資産の追加** ダイアログ ボックスが表示されます。  
  
4.  **型**一覧で、追加する拡張機能の種類を選択します。  
  
5.  (たとえば、項目テンプレートまたはコンパイル済みアセンブリ) は、現在のソリューションに含まれている拡張機能またはコンテンツ要素を追加するには、次の手順を実行します。  
  
    1.  **ソース**一覧で、選択**現在のソリューションでプロジェクトを**します。  
  
    2.  **プロジェクト**ボックスの一覧で、拡張機能の名前を選択します。  
  
    3.  **このフォルダーに埋め込む**ボックスに、資産を埋め込むし、選択するためのフォルダーの名前を入力、 **OK**ボタン。  
  
6.  拡張機能または現在のソリューションに含まれていないコンテンツの要素を追加するには、するには、次の手順を実行します。  
  
    1.  **ソース**ボックスの一覧で、**ファイル システム上の**します。  
  
    2.  **パス**フィールド、コンパイルまたは圧縮された拡張機能ファイルを完全なパスを入力するかを使用して、**参照**ファイルを参照するボタンをクリックします。  
  
    3.  **このフォルダーに埋め込む**ボックスに、資産を埋め込むし、選択するためのフォルダーの名前を入力、 **OK**ボタン。  
  
7.  パッケージに追加の拡張機能を含める場合は、同じ方法でそれらを追加します。  
  
8.  ソリューションをビルドします。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ビルド、 *.vsix* [Content_Types] VSIX のマニフェスト ファイルを含むファイル *.xml*ファイル、およびすべてのプロジェクトに追加した拡張機能資産。  
  
## <a name="see-also"></a>関連項目  
 [VSIX 拡張機能スキーマ 2.0 リファレンス](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Visual Studio 拡張機能の検索と使用](../ide/finding-and-using-visual-studio-extensions.md)