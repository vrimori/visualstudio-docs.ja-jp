---
title: "MSBuild プロジェクト ファイルでデータを保持します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロジェクト ファイル内のデータを永続化します。"
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# MSBuild プロジェクト ファイルでデータを保持します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

プロジェクトのサブタイプはデータをプロジェクト ファイルにサブタイプに固有の後で使用できるように保持する必要があります。  プロジェクトのサブタイプは次の要件を満たすためにプロジェクト ファイルの永続性が使用されます :  
  
1.  プロジェクトをビルドの一部として使用されるデータが保持されます。  \(Microsoft Build Engine の詳細については[MSBuild](http://msdn.microsoft.com/ja-jp/7c49aba1-ee6c-47d8-9de1-6f29a906e20b) を参照してください\)。ビルド関連の情報は次のいずれかあります :  
  
    1.  構成に依存しないデータ。  つまり空白またはその条件の MSBuild の要素に格納されているデータ。  
  
    2.  構成依存します。  つまり特定のプロジェクト構成に調整される MSBuild の要素に格納されているデータ。  次に例を示します。  
  
        ```  
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        ```  
  
2.  ビルド関連しないデータが保持されます。  このデータはXML スキーマに対して検証されない自由形式の XML で表すことができます。  
  
    1.  構成に依存しないデータ。  
  
    2.  構成依存します。  
  
## ビルド関連の情報の保持  
 プロジェクトのビルドに必要なデータの永続性は MSBuild によって処理されます。  MSBuild システムはビルド関連情報のマスター テーブルを保持します。  プロジェクトのサブタイプを取得するにはこのデータとプロパティの設定の値にアクセスを行います。  プロジェクトのサブタイプは保存する追加のプロパティを追加しプロパティを削除することでビルドに関するデータ テーブルを大きくすると保持されません。  
  
 MSBuild のデータを変更するにはプロジェクトのサブタイプは基本プロジェクト システム取得する必要があるから <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> して MSBuild のプロパティをオブジェクト。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> は `QueryInterface` を実行してそのための主要なプロジェクト システムおよび集計のプロジェクトのサブタイプのクエリで実装されるインターフェイスです。  
  
 次の手順では<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> を使用してプロパティを削除する手順について説明します。  
  
#### MSBuild のプロパティをプロジェクト ファイルから削除します。  
  
1.  プロジェクトのサブタイプの <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> の `QueryInterface` を呼び出します。  
  
2.  削除するプロパティに `pszPropName` の設定との呼び出しの <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A>。  
  
### 非永続化のビルドの関連情報  
 ビルドに重要ではないプロジェクト ファイル内のデータの永続性は<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> によって処理されます。  
  
 `project subtype aggregator` の主要な `project subtype project configuration` オブジェクトオブジェクトまたは両方の <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> を実行できます。  
  
 以下はビルドの関連情報の永続性に関する主要な概念について説明します。  
  
-   メイン プロジェクトのサブタイプ \(つまり最も外側のプロジェクトのサブタイプ\) アグリゲーター Foundation プロジェクトでは構成に依存しないデータの読み込みと保存にオブジェクトと構成に依存のデータの読み込みまたは保存するにはプロジェクトのサブタイプのプロジェクト構成オブジェクトでを呼び出します。  
  
-   基本プロジェクトはプロジェクトのサブタイプの集計の各レベルの <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> に複数のメソッドを呼び出して各レベルの GUID を渡します。  
  
-   基本プロジェクトは渡すかまたは特定のプロジェクトのサブタイプに専用の受信し集約レベル間の状態の永続化の方法としてこの機能を XML フラグメントを使用します。  
  
-   基本プロジェクトはGUID を渡す最も外側のプロジェクトのサブタイプの <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> の実装を呼び出します。  GUID が最も外側のプロジェクトのサブタイプに属している場合呼び出し自体を処理します ; それ以外の場合は内部のプロジェクトのサブタイプに GUID はに対応するプロジェクトのサブタイプが見つかるまで呼び出しなどに委任します。  
  
-   プロジェクトのサブタイプは内部のプロジェクトのサブタイプの呼び出しに転送する前または後に XML フラグメントを変更できます。  次の例はプロジェクトのサブタイプにプロジェクト ファイルの一部をプロジェクトのサブタイプに固有のプロパティを含むファイルの名前を渡す示します。  
  
    ```  
    <ProjectExtensions>  
        <VisualStudio>  
          <FlavorProperties GUID="{<FlavorGUID>}">  
            <FlavorProject TestFileFolder="TestFile" />  
          </FlavorProperties>  
        </VisualStudio>  
      </ProjectExtensions>  
    ```  
  
## 参照  
 [プロジェクトのサブタイプ](../../extensibility/internals/project-subtypes.md)