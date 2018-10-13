---
title: VSIX パッケージの構造 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 207abbda08134c2a1e065cf73050fc2451d4eaab
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49181461"
---
# <a name="anatomy-of-a-vsix-package"></a>VSIX パッケージの構造
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSIX パッケージは、分類、拡張機能をインストールして Visual Studio を使用してメタデータと共に、1 つまたは複数の Visual Studio 拡張を含む .vsix ファイルです。 そのメタデータは、VSIX マニフェストと [Content_Types] .xml ファイルに含まれます。 VSIX パッケージでは、ローカライズされたセットアップのテキストを提供する 1 つ以上の Extension.vsixlangpack ファイルを含めることもでき、依存関係をインストールする追加の VSIX パッケージを含めることができます。  
  
 VSIX パッケージの形式では、Open Packaging Conventions (OPC) 標準に従います。 パッケージには、バイナリが含まれていて、ファイルをサポートするには、[Content_Types] .xml ファイルと、.vsix マニフェスト ファイル。 1 つの VSIX パッケージには、複数のプロジェクトまたは複数のパッケージを独自のマニフェストの出力を含めることができます。  
  
> [!NOTE]
>  VSIX パッケージに含まれるファイルの名前は、スペースを含める必要がありますいないもとして Uniform Resource Identifier (URI) 内に予約されている文字の下で定義された[ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339)します。  
  
## <a name="the-vsix-manifest"></a>VSIX マニフェスト  
 VSIX マニフェストには、拡張機能のインストール、および次のように、VSX スキーマに関する情報が含まれています。 詳細については、次を参照してください。 [VSIX 拡張機能スキーマ 1.0 リファレンス](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)します。 VSIX マニフェストの例を次を参照してください。 [PackageManifest Element (Root Element, VSX Schema)](http://msdn.microsoft.com/en-us/f8ae42ba-775a-4d2b-976a-f556e147f187)します。  
  
 VSIX マニフェストを指定する必要があります`extension.vsixmanifest`.vsix ファイルに含まれています。  
  
## <a name="the-content"></a>コンテンツ  
 VSIX パッケージには、テンプレート、ツールボックス項目、Vspackage、またはその他の種類の Visual Studio でサポートされている拡張機能を含めることができます。  
  
## <a name="language-packs"></a>言語パック  
 VSIX パッケージには、1 回またはインストール中にローカライズされたテキストを提供する以上の Extension.vsixlangpack ファイルを含めることができます。 詳細については、次を参照してください。 [VSIX パッケージのローカライズ](../extensibility/localizing-vsix-packages.md)します。  
  
## <a name="dependencies-and-references"></a>依存関係および参照  
 VSIX パッケージでは、参照として他の VSIX パッケージを含めることができます。 独自の VSIX マニフェストの他の各パッケージがあります。  
  
 ユーザーは、依存関係がある拡張機能をインストールしようとすると、インストーラーは、ユーザー システムで、必要なアセンブリがインストールされていることを確認します。 必要なアセンブリが見つからない場合**拡張機能と更新**不足しているアセンブリの一覧を表示します。  
  
 1 つまたは複数の拡張機能マニフェストが含まれている場合[参照](http://msdn.microsoft.com/en-us/32c52934-e81e-4b53-8cb6-4df45ef7bfa8)要素、**拡張機能と更新**システムにインストールされている拡張機能への参照をそれぞれのマニフェストを比較し、インストール、インストールされていない場合は、拡張機能を参照します。 参照先の拡張機能の以前のバージョンがインストールされている場合、新しいバージョンに置き換わります。  
  
 マルチ プロジェクト ソリューション内のプロジェクトには、同じソリューションで別のプロジェクトへの参照が含まれている場合、VSIX パッケージには、そのプロジェクトの依存関係が含まれています。 この動作をオーバーライドするには、内部のプロジェクトをクリックでの参照 をクリックして、**プロパティ**ウィンドウで、設定、**出力の VSIX にグループが含まれる**プロパティを`BuiltProjectOutputGroup`。  
  
 VSIX パッケージ内の参照アセンブリのサテライト Dll を含めるには追加`SatelliteDllsProjectOutputGroup`を**出力の VSIX にグループが含まれる**プロパティ。  
  
## <a name="installation-location"></a>インストール場所  
 インストール中に、**拡張機能と更新**%localappdata%\microsoft\visualstudio\14.0\extensions 下のフォルダーに、VSIX パッケージの内容を検索します。  
  
 インストールは、既定では、%localappdata% がユーザー固有のディレクトリであるために、現在のユーザーにのみ適用されます。 ただし、設定した場合、 [AllUsers](http://msdn.microsoft.com/en-us/ac817f50-3276-4ddb-b467-8bbb1432455b)するマニフェストの要素`True`で、拡張機能がインストールされます.\\ *VisualStudioInstallationFolder*\Common7\IDE\Extensions コンピューターのすべてのユーザーに利用可能になります。  
  
## <a name="contenttypesxml"></a>[Content_Types] .xml  
 [Content_Types] .xml ファイルは .vsix 展開ファイルのファイルの種類を識別します。 Visual Studio は、パッケージのインストール中にこのファイルを使用しますが、ファイル自体ではインストールされません。 このファイルの詳細については、次を参照してください。 [、Content_types の構造\].xml ファイル](../extensibility/the-structure-of-the-content-types-dot-xml-file.md)します。  
  
 [Content_Types] .xml ファイルで、Open Packaging Conventions (OPC) 標準が必要です。 OPC の詳細については、次を参照してください。 [OPC: A 新しい標準のパッケージ化、データ](http://go.microsoft.com/fwlink/?LinkID=148207)MSDN Web サイト。

