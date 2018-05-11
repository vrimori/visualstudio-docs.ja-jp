---
title: VSIX パッケージの構造は |Microsoft ドキュメント
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
ms.openlocfilehash: d811c1539dde655657331b7ca3511bbd4e80063f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="anatomy-of-a-vsix-package"></a>VSIX パッケージの構造
VSIX パッケージは、Visual Studio は分類し、拡張機能のインストールを使用してメタデータと共に、1 つまたは複数の Visual Studio 拡張を含む .vsix ファイルです。 そのメタデータは、VSIX マニフェストと [Content_Types] .xml ファイルに含まれます。 VSIX パッケージでは、セットアップのローカライズされたテキストを提供する 1 つ以上の Extension.vsixlangpack ファイルを含めることがありますもと、依存関係をインストールする追加の VSIX パッケージを含めることがあります。  
  
 VSIX パッケージ形式では、Open Packaging Conventions (OPC) 標準に従います。 パッケージにバイナリが含まれています、ファイルをサポートするには、[Content_Types] .xml ファイルと、.vsix マニフェスト ファイル。 1 つの VSIX パッケージでは、複数のプロジェクト、またはを独自のマニフェストを持つ複数のパッケージの出力を含めることがあります。  
  
> [!NOTE]
>  VSIX パッケージに含まれるファイルの名前は、スペースを含める必要がありますいないもとして Uniform Resource Identifier (URI) 内に予約されている文字の下で定義された[ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339)です。  
  
## <a name="the-vsix-manifest"></a>VSIX マニフェスト  
 VSIX マニフェストには、拡張機能をインストールして次のように VSX Schema に関する情報が含まれています。 詳細については、次を参照してください。 [VSIX 拡張機能スキーマ 1.0 リファレンス](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)です。 VSIX マニフェストの例を次を参照してください。 [PackageManifest Element (Root Element, VSX Schema)](http://msdn.microsoft.com/en-us/f8ae42ba-775a-4d2b-976a-f556e147f187)です。  
  
 VSIX マニフェストを指定する必要があります`extension.vsixmanifest`.vsix ファイルに含まれているとします。  
  
## <a name="the-content"></a>コンテンツ  
 テンプレート、ツールボックス項目、Vspackage、またはその他の種類の Visual Studio でサポートされている拡張機能の VSIX パッケージを含めることがあります。  
  
## <a name="language-packs"></a>言語パック  
 1 回または複数の Extension.vsixlangpack ファイルのインストール時にローカライズされたテキストを提供するための VSIX パッケージがあります。 詳細については、次を参照してください。 [VSIX パッケージのローカライズ](../extensibility/localizing-vsix-packages.md)です。  
  
## <a name="dependencies-and-references"></a>依存関係および参照  
 VSIX パッケージでは、参照として他の VSIX パッケージを含めることがあります。 独自の VSIX マニフェストの他の各パッケージがあります。  
  
 ユーザーは、依存関係のある拡張機能をインストールしようとすると、インストーラーは、ユーザー システムに必要なアセンブリをインストールすることを確認します。 必要なアセンブリが見つからない場合**拡張機能と更新プログラム**不足しているアセンブリの一覧を表示します。  
  
 拡張機能マニフェストには、1 つまたは複数が含まれている場合[参照](http://msdn.microsoft.com/en-us/32c52934-e81e-4b53-8cb6-4df45ef7bfa8)要素、**拡張機能と更新**システムにインストールされている拡張機能への参照をそれぞれのマニフェストを比較し、インストール、インストールされていない場合は、拡張機能を参照します。 参照先の拡張機能の以前のバージョンがインストールされている場合、新しいバージョンに置き換わります。  
  
 複数プロジェクトのソリューション内のプロジェクトには、同じソリューション内の別のプロジェクトへの参照が含まれている場合、VSIX パッケージには、そのプロジェクトの依存関係が含まれています。 この動作をオーバーライドするには、内部のプロジェクトのし、[参照] をクリックして、**プロパティ**ウィンドウで、設定、**出力グループは、VSIX に含まれる**プロパティを`BuiltProjectOutputGroup`です。  
  
 VSIX パッケージ内の参照アセンブリのサテライト Dll を含めるには追加`SatelliteDllsProjectOutputGroup`を**出力グループは、VSIX に含まれる**プロパティです。  
  
## <a name="installation-location"></a>インストール場所  
 インストール中に、**拡張機能と更新プログラム**%localappdata%\microsoft\visualstudio\14.0\extensions 下のフォルダーに、VSIX パッケージの内容を検索します。  
  
 インストールは、既定では、%localappdata% はユーザー固有のディレクトリであるために、現在のユーザーにのみ適用されます。 ただし、設定した場合、 [AllUsers](http://msdn.microsoft.com/en-us/ac817f50-3276-4ddb-b467-8bbb1432455b)するマニフェストの要素`True`で、拡張機能がインストールされます.\\ *VisualStudioInstallationFolder*\Common7\IDE\Extensions コンピューターのすべてのユーザーに利用可能になります。  
  
## <a name="contenttypesxml"></a>[Content_Types] .xml  
 [Content_Types] .xml ファイルでは、展開された .vsix ファイルにファイルの種類を識別します。 Visual Studio では、パッケージのインストール中にこのファイルを使用しますが、ファイル自体ではインストールされません。 このファイルの詳細については、次を参照してください。 [[Content_types] .xml ファイルの構造](the-structure-of-the-content-types-dot-xml-file.md)です。  
  
 [Content_Types] .xml ファイルには、によって、Open Packaging Conventions (OPC) 標準が必要です。 OPC の詳細については、次を参照してください。 [OPC: A 新しい標準のパッケージ化、データ](http://go.microsoft.com/fwlink/?LinkID=148207)MSDN Web サイトです。