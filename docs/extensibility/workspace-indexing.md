---
title: Visual Studio でのインデックス作成ワークスペース |Microsoft Docs
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3163e98c-1c79-48a7-813f-7923be894ba1
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 5004db0d895d1fdc697c18606c346c24cd484527
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939151"
---
# <a name="workspace-indexing"></a>ワークスペースのインデックス作成

ソリューションでは、プロジェクト システムはビルドの機能を提供する担当、デバッグ、 **GoTo**シンボルの検索、および詳細。 プロジェクト システムは、関係およびプロジェクト内のファイルの機能を理解しているこの操作を行うことができます。 [フォルダーを開く](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)ワークスペースには、豊富な IDE 機能も提供する同じ情報を得ることが必要があります。 コレクションとこのデータの永続的なストレージは、ワークスペースのインデックスと呼ばれるプロセスです。 このインデックス付きデータは、一連の非同期 Api を使って照会できます。 エクステンダーが提供することで、インデックス作成プロセスに参加できる<xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner>特定の種類のファイルを処理する方法を理解します。

## <a name="types-of-indexed-data"></a>インデックス付きデータの種類

インデックスが作成されるデータの 3 種類があります。 注ファイル スキャナーからの型は、インデックスから逆シリアル化の種類によって異なります。

|データ|スキャナーの種類のファイル|インデックスのクエリ結果の種類|関連する型|
|--|--|--|--|
|参照|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|シンボル|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> 代わりに使用する必要があります`IIndexWorkspaceService`クエリ|
|データ値|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>インデックス付きデータの照会

永続化されたデータへのアクセスに使用できる 2 つの非同期型があります。 最初は<xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData>します。 1 つのファイルの基本的なアクセスを提供`FileReferenceResult`と`FileDataResult`データ、およびその結果をキャッシュします。 2 つ目は、<xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService>はクエリ機能の詳細については、キャッシュを使用しません。

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Indexing;

private static IIndexWorkspaceData GetCachedIndexedData(IWorkspace workspace)
{
    // Gets access to indexed data wrapped in a cache.
    return workspace?.GetIndexWorkspaceDataService()?.CreateIndexWorkspaceData();
}

private static IIndexWorkspaceService GetDirectIndexedData(IWorkspace workspace)
{
    // Gets direct access to indexed data.
    // Can also be casted to IIndexWorkspaceService2.
    return workspace?.GetIndexWorkspaceService();
}
```

## <a name="participating-in-indexing"></a>インデックス作成に参加しています。

ワークスペースのインデックス作成では、次のシーケンスほぼ次に示します。

1. 検出と (初期開始スキャン) でのみ、ワークスペース内のファイル システム エンティティの永続化します。
1. スキャンするファイルあたり最高の優先順位で一致するプロバイダーがよく寄せられる`FileReferenceInfo`秒。
1. スキャンするファイルあたり最高の優先順位で一致するプロバイダーがよく寄せられる`SymbolDefinition`秒。
1. すべてのプロバイダーは求め、1 ファイル`FileDataValue`秒。

拡張機能が実装することで、スキャナーをエクスポートできます`IWorkspaceProviderFactory<IFileScanner>`を持つ型をエクスポートおよび<xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute>します。 `SupportedTypes`属性引数は 1 つまたは複数の値から<xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants>します。 例スキャナーでは、VS SDK を参照してください。[サンプル](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs)します。

> [!WARNING]
> サポートするファイルのスキャナーをエクスポートしないで、`FileScannerTypeConstants.FileScannerContentType`型。 Microsoft 内部用でのみ使用されます。

高度な状況は、拡張機能は任意のファイルの種類のセットをサポートして動的に可能性があります。 MEF エクスポートではなく`IWorkspaceProviderFactory<IFileScanner>`、拡張機能をエクスポートできます`IWorkspaceProviderFactory<IFileScannerProvider>`します。 このファクトリ型がインポートする、インスタンス化し、がインデックス作成の開始時にその<xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A>メソッドが呼び出されます。 `IFileScanner` 任意の値をサポートしているインスタンス`FileScannerTpeConstants`は受け入れられます、だけでなくシンボルします。

## <a name="next-steps"></a>次の手順

* [ワークスペースと言語サービス](workspace-language-services.md)-、ワークスペースを開いているフォルダーに言語サービスを統合する方法について説明します。
* [ワークスペース ビルド](workspace-build.md)-フォルダーを開くサポートは、MSBuild とメイクファイルなどのシステムを構築します。