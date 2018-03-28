---
title: Visual Studio でのインデックス作成ワークスペース |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/21/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3163e98c-1c79-48a7-813f-7923be894ba1
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 9bf3a094184e2d57b4a066234d84a6ab6380510b
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2018
---
# <a name="workspace-indexing"></a>ワークスペースのインデックス

ソリューションでは、プロジェクト システムは、ビルドの機能を提供するため、デバッグ、 **GoTo**シンボルは、次の検索、および詳細。 プロジェクト システムは、リレーションシップと、プロジェクト内のファイルの機能を理解しているために、この作業を実行できます。 [フォルダーを開く](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)ワークスペースには、豊富な IDE 機能も提供する同じ情報を得ることが必要があります。 コレクションとこのデータの永続的な記憶域は、ワークスペースのインデックスと呼ばれるプロセスです。 一連の非同期 Api は、このインデックス付きデータを照会できます。 エクステンダーが提供することにより、インデックス作成プロセスに参加できる<xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner>特定の種類のファイルを処理する方法を知っています。

## <a name="types-of-indexed-data"></a>インデックス付きデータの種類

インデックスが作成されるデータの 3 種類があります。 注ファイル スキャナーから予期される型は、インデックスから逆シリアル化の種類によって異なります。

|データ|スキャナーの種類のファイル|インデックスのクエリ結果型|関連する型|
|--|--|--|--|
|参照|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|シンボル|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> 代わりに使用する必要があります`IIndexWorkspaceService`クエリ|
|データ値|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>インデックス付きデータのクエリ

永続化されたデータにアクセスする使用可能な 2 つの非同期の種類があります。 最初はを通じて<xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData>です。 1 つのファイルの基本的なアクセスを提供`FileReferenceResult`と`FileDataResult`データ、およびその結果をキャッシュします。 2 番目は、<xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService>キャッシュを使用しませんが、詳細の照会機能では、います。

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

## <a name="participating-in-indexing"></a>インデックスに参加しています。

インデックスの作成 ワークスペースでは、次のシーケンスほぼ次に示します。

1. 探索、(初期開始スキャン) の場合のみ、ワークスペース内のファイル システム エンティティの永続化します。
1. スキャンする優先順位が高い一致するプロバイダーを求め、ファイルあたり`FileReferenceInfo`s。
1. スキャンする優先順位が高い一致するプロバイダーを求め、ファイルあたり`SymbolDefinition`s。
1. 1 ファイルでは、すべてのプロバイダーはの求められます`FileDataValue`s。

拡張機能が実装することで、スキャナーをエクスポートできます`IWorkspaceProviderFactory<IFileScanner>`を持つ型をエクスポートおよび<xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute>です。 `SupportedTypes`属性引数がから 1 つ以上の値にする必要があります<xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants>です。 例スキャナーでは、VS SDK を参照してください。[サンプル](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs)です。

> [!WARNING]
> サポートするファイルのスキャナーをエクスポートしないで、`FileScannerTypeConstants.FileScannerContentType`型です。 Microsoft 内部目的のみ使用されます。

高度な状況は、拡張機能はファイルの種類の任意のセットを動的にサポート可能性があります。 MEF エクスポートではなく`IWorkspaceProviderFactory<IFileScanner>`、拡張機能がエクスポートできる`IWorkspaceProviderFactory<IFileScannerProvider>`です。 インデックス作成の開始時にこのファクトリの型はインポートする、インスタンス化されがその<xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A>メソッドが呼び出されました。 `IFileScanner` インスタンスから任意の値をサポートする`FileScannerTpeConstants`が有効である、だけでなくシンボルします。

## <a name="next-steps"></a>次の手順

* [ワークスペースおよび言語サービス](workspace-language-services.md)-言語サービス フォルダーを開くには、ワークスペースを統合する方法について説明します。
* [ワークスペース ビルド](workspace-build.md)-MSBuild とメイクファイルなどのシステムをビルド フォルダーを開く。