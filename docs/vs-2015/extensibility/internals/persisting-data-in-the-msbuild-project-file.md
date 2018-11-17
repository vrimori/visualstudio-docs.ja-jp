---
title: MSBuild プロジェクト ファイルでデータの保持 |Microsoft Docs
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
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 059ddc7b9b8fe0de06530af704bb5f7e271f6744
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749639"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>MSBuild プロジェクト ファイルでのデータの保持
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

プロジェクト サブタイプは、後で使用するためのプロジェクト ファイルにサブタイプ固有のデータを保持する必要があります。 プロジェクト サブタイプは、次の要件を満たすためにプロジェクト ファイルの永続化を使用します。  
  
1.  プロジェクトのビルドの一部として使用されるデータを保持します。 (Microsoft Build Engine の詳細については、次を参照してください[MSBuild](http://msdn.microsoft.com/en-us/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)。)。ビルド関連の情報を実行できますか。  
  
    1.  構成に依存しないデータ。 つまり、空白または不足している条件を持つ MSBuild 要素に格納されているデータ。  
  
    2.  構成に依存するデータ。 つまり、データが、特定のプロジェクト構成を規定する MSBuild 要素に格納されています。 例えば:  
  
        ```  
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        ```  
  
2.  ビルドには関係ないデータを保持します。 このデータは、XML スキーマに対して検証されていない自由形式の XML で表現できます。  
  
    1.  構成に依存しないデータ。  
  
    2.  構成に依存するデータ。  
  
## <a name="persisting-build-related-information"></a>ビルドに関連する情報の保存  
 プロジェクトのビルドに役立つデータの永続化は、MSBuild によって処理されます。 MSBuild システムでは、ビルドに関連する情報のマスター テーブルを保持します。 プロジェクト サブタイプは、プロパティ値を取得および設定は、このデータにアクセスする責任を負います。 プロジェクト サブタイプは、永続化する追加のプロパティを追加することは保存されませんので、プロパティを削除することで、ビルドに関連するデータ テーブルを補強もできます。  
  
 MSBuild データを変更するにはプロジェクトのサブタイプはにより、基本プロジェクト システムから、MSBuild プロパティ オブジェクトを取得する責任を負います<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>します。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 実行して、そのコア プロジェクト システムと集計のプロジェクト サブタイプのクエリで実装されるインターフェイスは、`QueryInterface`します。  
  
 次の手順を使用してプロパティを削除する手順の概要を<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>します。  
  
#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>MSBuild プロジェクト ファイルからプロパティを削除するには  
  
1.  呼び出す`QueryInterface`で<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>のプロジェクト サブタイプ。  
  
2.  呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A>で`pszPropName`を削除するプロパティに設定します。  
  
### <a name="persisting-non-build-related-information"></a>関連情報を永続化非ビルド  
 ビルドには関係ありませんプロジェクト ファイル内のデータの永続化はを通じて処理<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>します。  
  
 実装できます<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>、メイン`project subtype aggregator`オブジェクト、`project subtype project configuration`オブジェクト、またはその両方です。  
  
 次の点では、非ビルド関連情報の永続化に関する主要な概念を説明します。  
  
-   読み込みし、構成の独立したデータを保存するメイン プロジェクトのサブタイプ (つまり、最も外側にあるプロジェクトのサブタイプ) アグリゲーター オブジェクトの基本プロジェクトを呼び出すし、プロジェクト サブタイプ プロジェクトの構成オブジェクトの読み込みまたは保存の構成に依存するを呼び出しますデータ。  
  
-   ベースのプロジェクトのメソッドを呼び出して、<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>複数のプロジェクト サブタイプの集計の各レベルには時刻および各レベルの GUID を渡します。  
  
-   ベースのプロジェクトでは、渡すか、特定のプロジェクト サブタイプには専用であり、集計レベルの間の状態を保持する方法として、このメカニズムを使用する XML フラグメントを受け取る。  
  
-   基本プロジェクト呼び出しの最も外側のプロジェクト サブタイプの<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>実装の GUID を渡します。 呼び出し自体を処理、GUID が最も外側のプロジェクト サブタイプに所属している場合それ以外の場合、GUID に対応するプロジェクトのサブタイプが見つかるまで、内部のプロジェクト サブタイプ、およびへの呼び出しを委任します。  
  
-   プロジェクト サブタイプの前に、または後、内部のプロジェクト サブタイプに呼び出しを代行 XML フラグメントを変更できます。 次の例では、そのプロジェクト サブタイプに渡されたはプロジェクトのサブタイプに固有のプロパティを含むファイルの名前、プロジェクト ファイルからの抜粋を示します。  
  
    ```  
    <ProjectExtensions>  
        <VisualStudio>  
          <FlavorProperties GUID="{<FlavorGUID>}">  
            <FlavorProject TestFileFolder="TestFile" />  
          </FlavorProperties>  
        </VisualStudio>  
      </ProjectExtensions>  
    ```  
  
## <a name="see-also"></a>関連項目  
 [プロジェクト サブタイプ](../../extensibility/internals/project-subtypes.md)

