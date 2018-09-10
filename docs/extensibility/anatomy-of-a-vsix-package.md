---
title: VSIX パッケージの構造 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f5c60e0b812cd0557b266d3e34dae62cb22cc57d
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44281757"
---
# <a name="anatomy-of-a-vsix-package"></a>VSIX パッケージの構造
VSIX パッケージは、 *.vsix*メタデータ Visual Studio と共に、1 つまたは複数の Visual Studio 拡張が含まれるファイルを使用して分類および拡張機能をインストールします。 そのメタデータが含まれている VSIX マニフェストで、 *[Content_Types] .xml*ファイル。 1 つまたは複数が、VSIX パッケージに含めることもできます*Extension.vsixlangpack*を提供するファイルがローカライズされたセットアップのテキストと、依存関係をインストールする追加の VSIX パッケージを含めることができます。  
  
 VSIX パッケージの形式では、Open Packaging Conventions (OPC) 標準に従います。 パッケージと共にバイナリやサポート ファイルに含まれる、 *[Content_Types] .xml*ファイルと *.vsix*マニフェスト ファイル。 1 つの VSIX パッケージには、複数のプロジェクトまたは複数のパッケージを独自のマニフェストの出力を含めることができます。  
  
> [!NOTE]
>  VSIX パッケージに含まれるファイルの名前は、スペースを含める必要がありますいないもとして Uniform Resource Identifier (URI) 内に予約されている文字の下で定義された[ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339)します。  
  
## <a name="the-vsix-manifest"></a>VSIX マニフェスト  
 VSIX マニフェストには、拡張機能のインストール、および次のように、VSX スキーマに関する情報が含まれています。 詳細については、次を参照してください。 [VSIX 拡張機能スキーマ 1.0 リファレンス](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)します。 VSIX マニフェストの例を次を参照してください。 [PackageManifest element (ルート element, VSX schema)](https://msdn.microsoft.com/library/f8ae42ba-775a-4d2b-976a-f556e147f187)します。  
  
 VSIX マニフェストを指定する必要があります`extension.vsixmanifest`に含まれる、^ .vsix * ファイル。  
  
## <a name="the-content"></a>コンテンツ  
 VSIX パッケージには、テンプレート、ツールボックス項目、Vspackage、またはその他の種類の Visual Studio でサポートされている拡張機能を含めることができます。  
  
## <a name="language-packs"></a>言語パック  
 VSIX パッケージは、1 回以上を含めることができます*Extension.vsixlangpack*ファイルをインストール中にローカライズされたテキストを提供します。 詳細については、次を参照してください。[ローカライズ VSIX パッケージ](../extensibility/localizing-vsix-packages.md)します。  
  
## <a name="dependencies-and-references"></a>依存関係および参照  
 VSIX パッケージでは、参照として他の VSIX パッケージを含めることができます。 独自の VSIX マニフェストの他の各パッケージがあります。  
  
 ユーザーは、依存関係がある拡張機能をインストールしようとすると、インストーラーは、ユーザー システムで、必要なアセンブリがインストールされていることを確認します。 必要なアセンブリが見つからない場合**拡張機能と更新**不足しているアセンブリの一覧を表示します。  
  
 1 つまたは複数の拡張機能マニフェストが含まれている場合[参照](/previous-versions/visualstudio/visual-studio-2010/dd393687(v=vs.100))要素、**拡張機能と更新**システムにインストールされている拡張機能への参照をそれぞれのマニフェストを比較し、インストール、インストールされていない場合は、拡張機能を参照します。 参照先の拡張機能の以前のバージョンがインストールされている場合、新しいバージョンに置き換わります。  
  
 マルチ プロジェクト ソリューション内のプロジェクトには、同じソリューションで別のプロジェクトへの参照が含まれている場合、VSIX パッケージには、そのプロジェクトの依存関係が含まれています。 この動作をオーバーライドするには、内部のプロジェクトをクリックでの参照 をクリックして、**プロパティ**ウィンドウで、設定、**出力の VSIX にグループが含まれる**プロパティを`BuiltProjectOutputGroup`。  
  
 VSIX パッケージ内の参照アセンブリのサテライト Dll を含めるには追加`SatelliteDllsProjectOutputGroup`を**出力の VSIX にグループが含まれる**プロパティ。  
  
## <a name="installation-location"></a>インストール場所  
 インストール中に、**拡張機能と更新**下のフォルダーに、VSIX パッケージの内容を探します *%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions*します。  
  
 既定では、インストールにのみ適用されます、現在のユーザーのため *%localappdata%* はユーザー固有のディレクトリです。 ただし、設定した場合、 [AllUsers](https://msdn.microsoft.com/library/ac817f50-3276-4ddb-b467-8bbb1432455b)するマニフェストの要素`True`で、拡張機能がインストールされます *.\\* VisualStudioInstallationFolder*\Common7\IDE\Extensions*コンピューターのすべてのユーザーに利用可能になります。  
  
## <a name="contenttypesxml"></a>[Content_Types] .xml  
 *[Content_Types] .xml*ファイルが展開済みファイルの種類を識別する *.vsix*ファイル。 Visual Studio は、パッケージのインストール中にこのファイルを使用しますが、ファイル自体ではインストールされません。 このファイルの詳細については、次を参照してください。 [[Content_types] .xml ファイルの構造](the-structure-of-the-content-types-dot-xml-file.md)します。  
  
 A *[Content_Types] .xml* Open Packaging Conventions (OPC) 標準でファイルが必要です。 OPC の詳細については、次を参照してください。 [OPC: データをパッケージ化するための新しい標準](https://blogs.msdn.microsoft.com/msdnmagazine/2007/08/08/opc-a-new-standard-for-packaging-your-data/)MSDN Web サイト。