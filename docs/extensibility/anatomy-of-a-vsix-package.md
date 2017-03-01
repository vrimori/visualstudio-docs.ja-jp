---
title: "VSIX パッケージの分析 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 7278fb37984b92a6a07823c552db5c59a446d0d2
ms.openlocfilehash: 633db03670180ac83c5c936f66953fb38d4ebd67
ms.lasthandoff: 02/22/2017

---
# <a name="anatomy-of-a-vsix-package"></a>VSIX パッケージの構造
VSIX パッケージは、分類、および拡張機能をインストールする Visual Studio を使用してメタデータと共に、1 つまたは複数の Visual Studio 拡張を含む .vsix ファイルです。 そのメタデータは、VSIX マニフェストおよび [Content_Types] .xml ファイルに含まれます。 VSIX パッケージでは、セットアップのローカライズされたテキストを提供する&1; つ以上の Extension.vsixlangpack ファイルを含めることもでき、依存関係をインストールする追加の VSIX パッケージを含めることがします。  
  
 VSIX パッケージ形式では、Open Packaging Conventions (OPC) 標準に従います。 パッケージにバイナリが含まれていて、ファイルをサポートするには、[Content_Types] .xml ファイルと、.vsix マニフェスト ファイル。 1 つの VSIX パッケージには、複数のプロジェクトまたは複数のパッケージを独自のマニフェストの出力を含めることができます。  
  
> [!NOTE]
>  VSIX パッケージに含まれるファイルの名前は、スペースを含めないでくださいも下にあるとして Uniform Resource Identifier (URI) 内に予約されている文字が定義されている[ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339)します。  
  
## <a name="the-vsix-manifest"></a>VSIX マニフェスト  
 VSIX マニフェストには、拡張機能をインストールして次のように、VSX スキーマに関する情報が含まれています。 詳細については、次を参照してください。 [VSIX 拡張機能スキーマ 1.0 リファレンス](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)します。 例 VSIX マニフェストの場合は、次を参照してください。 [PackageManifest 要素 (ルート要素、VSX スキーマ)](http://msdn.microsoft.com/en-us/f8ae42ba-775a-4d2b-976a-f556e147f187)します。  
  
 VSIX マニフェストに指定する必要があります`extension.vsixmanifest`.vsix ファイルに含まれているとします。  
  
## <a name="the-content"></a>コンテンツ  
 VSIX パッケージには、テンプレート、ツールボックス アイテムの選択、vspackages にある、またはその他の Visual Studio でサポートされている拡張機能の種類を含めることができます。  
  
## <a name="language-packs"></a>言語パック  
 1 回または複数の Extension.vsixlangpack ファイルのインストール中にローカライズされたテキストを提供するための VSIX パッケージがあります。 詳細については、次を参照してください。 [VSIX パッケージのローカライズ](../extensibility/localizing-vsix-packages.md)します。  
  
## <a name="dependencies-and-references"></a>依存関係および参照  
 VSIX パッケージでは、参照として、他の VSIX パッケージを含めることができます。 独自の VSIX マニフェストの他の各パッケージがあります。  
  
 ユーザーは、依存関係がある拡張機能をインストールしようとすると、インストーラーは、必要なアセンブリがユーザーのシステムにインストールされていることを確認します。 必要なアセンブリが見つからない場合**拡張機能と更新プログラム**不足しているアセンブリの一覧を表示します。  
  
 拡張機能マニフェストには、1 つまたは複数が含まれている場合[参照](http://msdn.microsoft.com/en-us/32c52934-e81e-4b53-8cb6-4df45ef7bfa8)要素、**拡張機能と更新プログラム**システムにインストールされている拡張機能への参照のマニフェストを比較し、インストールされていない場合は、参照先の拡張機能をインストールします。 参照されている拡張機能の以前のバージョンがインストールされている場合、新しいバージョンに置き換わります。  
  
 複数プロジェクトのソリューション内のプロジェクトには、同じソリューションで別のプロジェクトへの参照が含まれている場合、VSIX パッケージには、そのプロジェクトの依存関係が含まれています。 この動作をオーバーライドするには、内部のプロジェクトのしてから、[参照] をクリックして、**プロパティ**ウィンドウで、設定、**出力グループは、VSIX に含まれる**プロパティを`BuiltProjectOutputGroup`します。  
  
 VSIX パッケージ内の参照アセンブリのサテライト Dll を組み込むには追加`SatelliteDllsProjectOutputGroup`に、**出力グループは、VSIX に含まれる**プロパティです。  
  
## <a name="installation-location"></a>インストール場所  
 インストール中に、**拡張機能と更新プログラム**%localappdata%\microsoft\visualstudio\14.0\extensions 下のフォルダーに VSIX パッケージの内容を検索します。  
  
 インストールは、既定では、%localappdata% がユーザー固有のディレクトリであるために、現在のユーザーにのみ適用されます。 ただし、設定した場合、 [AllUsers](http://msdn.microsoft.com/en-us/ac817f50-3276-4ddb-b467-8bbb1432455b)するマニフェストの要素`True`で、拡張機能がインストールされます.\\ *VisualStudioInstallationFolder*\Common7\IDE\Extensions コンピューターのすべてのユーザーを使用することができます。  
  
## <a name="contenttypesxml"></a>[Content_Types] .xml  
 [Content_Types] .xml ファイルでは、展開された .vsix ファイルにファイルの種類を識別します。 Visual Studio では、パッケージのインストール時にこのファイルを使用しますが、ファイル自体はインストールされません。 このファイルの詳細については、次を参照してください。 [[Content_types] .xml ファイルの構造](the-structure-of-the-content-types-dot-xml-file.md)します。  
  
 [Content_Types] .xml ファイルが必要で、Open Packaging Conventions (OPC) 標準です。 OPC の詳細については、次を参照してください。 [OPC: A 新しい標準のパッケージ化、データ](http://go.microsoft.com/fwlink/?LinkID=148207)MSDN Web サイトです。
