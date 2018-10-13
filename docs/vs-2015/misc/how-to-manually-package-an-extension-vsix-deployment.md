---
title: '方法: 拡張機能 (VSIX 配置) を手動でパッケージ化 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d25990e0-e782-4a79-9d9a-1caf3c56c6a2
caps.latest.revision: 10
manager: douge
ms.openlocfilehash: ad93bfe700c881977130ba6651bd3e271207a56f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49269309"
---
# <a name="how-to-manually-package-an-extension-vsix-deployment"></a>方法: 拡張機能を手動でパッケージ化する (VSIX 配置)
VSIX パッケージを作成して、配置用の [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 拡張機能をラップすることができます。 パッケージを作成するには、3 つの方法があります。  
  
-   [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] SDK に含まれている機能拡張テンプレートのいずれかを使用して、VSIX パッケージ プロジェクトを作成します。 これは、ほとんどのシナリオで最も簡単なオプションです。  
  
-   拡張プロジェクトの出力を空の [VSIX プロジェクト](../extensibility/vsix-project-template.md)でラップします。 テンプレート、サポートされていないアセンブリおよびカスタム型には、このオプションをお勧めします。  
  
-   VSIX パッケージを手動で作成します。 このオプションは、その他の 2 つのオプションが利用できない場合にのみお勧めします。  
  
 ここでは、3 つ目のオプションについて説明します。  
  
## <a name="creating-a-vsix-package"></a>VSIX パッケージの作成  
 拡張機能を手動でパッケージ化するには、extension.manifest ファイルと [Content_Types].xml ファイルを拡張機能プロジェクトに追加し、ビルド出力と一緒に圧縮ファイルに含め、.vsix ファイル名拡張子を持つように圧縮ファイルの名前を変更します。 パッケージ化する拡張機能は、 [VSIX スキーマ](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)でサポートされている種類のものである必要があります。  
  
> [!NOTE]
>  VSIX パッケージ内のファイル名では、スペースを含める必要がありますいないもとして Uniform Resource Identifier (URI) 内に予約されている文字の下で定義された[ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339)します。  
  
#### <a name="to-manually-create-a-vsix-package"></a>VSIX パッケージを手動で作成するには  
  
1.  VSIX スキーマでサポートされている型の Visual Studio 拡張機能を作成します。  
  
2.  XML ファイルを作成し、 `extension.vsixmanifest`という名前を付けます。  
  
3.  VSIX スキーマに従って extension.vsixmanifest ファイルを入力します。 マニフェストの例については、「 [PackageManifest Element (Root Element, VSX Schema)](http://msdn.microsoft.com/en-us/f8ae42ba-775a-4d2b-976a-f556e147f187)」を参照してください。  
  
4.  2 つ目の XML ファイルを作成し、 `[Content_Types].xml`という名前を付けます。  
  
5.  [Content_Types] .xml ファイルで指定されている入力[、Content_types の構造\].xml ファイル](../extensibility/the-structure-of-the-content-types-dot-xml-file.md)します。  
  
6.  ディレクトリ内に、配置する拡張機能と共に、両方の XML ファイルを配置します。  
  
     プロジェクト テンプレートや項目テンプレートでは、XML ファイルと同じフォルダーにテンプレートを含む .zip ファイルを配置します。 .zip ファイルに XML ファイルを配置しないでください。  
  
     その他のすべての場合においては、ビルド出力と同じディレクトリに XML ファイルを配置します。  
  
7.  Windows エクスプローラーで、拡張コンテンツと 2 つの XML ファイルを含むフォルダーを右クリックし、 **[送信]** をクリックして、 **[圧縮 (zip 形式) フォルダー]** をクリックします。  
  
8.  結果として得られる .zip ファイルの名前を *Filename*.vsix に変更します。ここで *Filename* には、パッケージをインストールする再頒布可能なファイルの名前を指定します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio 拡張機能を配布](../extensibility/shipping-visual-studio-extensions.md)   
 [VSIX パッケージの構造](../extensibility/anatomy-of-a-vsix-package.md)   
 [PackageManifest Element (Root Element, VSX Schema)](http://msdn.microsoft.com/en-us/f8ae42ba-775a-4d2b-976a-f556e147f187)