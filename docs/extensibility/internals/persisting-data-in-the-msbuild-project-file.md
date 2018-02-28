---
title: "MSBuild プロジェクト ファイルでデータの永続化 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b2bb73602a6cba07fe9cbde4ddae4219f5a2b350
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>MSBuild プロジェクト ファイルでデータを保持します。
プロジェクトのサブタイプは、後で使用できるプロジェクト ファイルにサブタイプに固有のデータを保持する必要があります。 プロジェクトのサブタイプでは、プロジェクト ファイルの永続化を使用して、次の要件を満たします。  
  
1.  プロジェクトのビルドの一部として使用されるデータを保持します。 (Microsoft Build Engine の詳細については、次を参照してください[MSBuild](../../msbuild/msbuild.md)。)。ビルド関連の情報をするか、実行できます。  
  
    1.  構成に依存しないデータ。 つまり、空白または不足している条件を持つ MSBuild 要素に格納されているデータ。  
  
    2.  構成に依存するデータ。 つまり、データを特定のプロジェクト構成には、規定 MSBuild 要素に格納します。 例:  
  
        ```  
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        ```  
  
2.  ないビルドに関連するデータを保持します。 XML スキーマに対して検証されません自由形式の XML では、このデータを表現することができます。  
  
    1.  構成に依存しないデータ。  
  
    2.  構成に依存するデータ。  
  
## <a name="persisting-build-related-information"></a>ビルド関連の情報を永続化します。  
 プロジェクトを作成するために役立つデータの永続化は、MSBuild によって処理されます。 MSBuild システムでは、ビルドに関連する情報のマスター テーブルを保持します。 プロジェクトのサブタイプでは、このデータを取得し、プロパティ値の設定にアクセスする担当します。 永続化する他のプロパティを追加することは保存されませんので、プロパティを削除することで、プロジェクトのサブタイプはビルドに関連するデータ テーブルを強化もできます。  
  
 MSBuild のデータを変更するには、プロジェクトのサブタイプは、により、基本プロジェクト システムから MSBuild プロパティ オブジェクトを取得するため<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>です。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>実行してそのコア プロジェクト システムと集計のプロジェクト サブタイプ クエリで実装されるインターフェイスは、`QueryInterface`です。  
  
 次の手順を使用してプロパティを削除する手順の概要<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>です。  
  
#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>MSBuild プロジェクト ファイルからプロパティを削除するには  
  
1.  呼び出す`QueryInterface`で<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>のプロジェクトのサブタイプ。  
  
2.  呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A>で`pszPropName`を削除するプロパティを設定します。  
  
### <a name="persisting-non-build-related-information"></a>永続化非ビルド関連情報  
 ビルドには重要ではないプロジェクト ファイル内のデータの持続性がによって処理される<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>です。  
  
 実装できます<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>、メイン`project subtype aggregator`オブジェクト、`project subtype project configuration`オブジェクト、またはその両方です。  
  
 次の点では、非ビルド関連情報の永続化に関する主な概念を説明します。  
  
-   読み込んで、構成の独立したデータを保存するメイン プロジェクトのサブタイプ (つまり、最も外側にあるプロジェクトのサブタイプ) アグリゲーター オブジェクトの基本プロジェクトを呼び出すし、プロジェクトのサブタイプ プロジェクト構成オブジェクトの読み込みまたは依存構成を保存する上で呼び出しますデータ。  
  
-   基本のプロジェクトのメソッドを呼び出して、<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>複数のプロジェクト サブタイプの集計の各レベルには時刻および各レベルに対応する GUID を渡します。  
  
-   基本のプロジェクトでは、成功または専用の特定のプロジェクト サブタイプ、集計レベルの間で状態を保持する手段としてこのメカニズムを使用して XML フラグメントを受信します。  
  
-   基本のプロジェクトを呼び出す最も外側にあるプロジェクトのサブタイプの<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>実装の GUID を渡します。 自体、呼び出しを処理する場合は、GUID は、最も外側にあるプロジェクトのサブタイプに属する、それ以外の場合、GUID に対応するプロジェクトのサブタイプが見つかるまで、内部のプロジェクト サブタイプに呼び出しを委任します。  
  
-   プロジェクトのサブタイプは、内部のプロジェクト サブタイプへの呼び出しを代行させる後または前に XML フラグメントを変更することもします。 次の例では、そのプロジェクトのサブタイプに渡されたはプロジェクトのサブタイプに固有のプロパティを含むファイルの名前は、プロジェクト ファイルからの抜粋を示します。  
  
    ```  
    <ProjectExtensions>  
        <VisualStudio>  
          <FlavorProperties GUID="{<FlavorGUID>}">  
            <FlavorProject TestFileFolder="TestFile" />  
          </FlavorProperties>  
        </VisualStudio>  
      </ProjectExtensions>  
    ```  
  
## <a name="see-also"></a>参照  
 [プロジェクト サブタイプ](../../extensibility/internals/project-subtypes.md)