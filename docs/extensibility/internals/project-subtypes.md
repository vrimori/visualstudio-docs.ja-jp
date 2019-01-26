---
title: プロジェクトのサブタイプ |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c2e5151131efdab36a3c9e5cf646b1ca9bf94b5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922718"
---
# <a name="project-subtypes"></a>プロジェクト サブタイプ
プロジェクト サブタイプを使用すると、flavor のプロジェクト システムの動作をカスタマイズまたは[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。 カスタマイズが可能で、プロジェクト ファイル内の項目をフィルター処理を追加または追加のデータを保存、**新しい項目の追加** ダイアログ ボックスで、アセンブリのデバッグ方法と、展開方法を制御して、プロジェクトの拡張**プロパティページ** ダイアログ ボックス。 Vspackage では、COM の集計を使用してプロジェクトのサブタイプを実装します。  
  
> [!NOTE]
>  Visual C プロジェクト システムは、プロジェクトのサブタイプをサポートしていません。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 自体は、プロジェクトのサブタイプを使用して、SQL Server とスマート デバイス プロジェクトを実装します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [プロジェクト サブタイプのデザイン](../../extensibility/internals/project-subtypes-design.md)  
 プロジェクト サブタイプの概念について説明します。  
  
 [プロジェクト サブタイプの初期化シーケンス](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 によってプログラムのプロジェクト サブタイプの初期化シーケンスをについて説明します。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境。  
  
 [プロジェクト サブタイプによって拡張されるプロパティとメソッド](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 プロジェクト サブタイプを使用して、最も頻繁に拡張メソッド、機能の詳細な説明を提供します。  
  
 [MSBuild プロジェクト ファイルでのデータの保持](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 プロジェクト ファイル内のデータを永続化する方法と使用方法について説明します<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>プロジェクト サブタイプの集計レベルの間でプロジェクト ファイル内のデータを維持します。  
  
 [プロジェクト プロパティのユーザー インターフェイス](../../extensibility/internals/project-property-user-interface.md)  
 プロジェクト サブタイプが、プロジェクトを変更する方法について説明します。**プロパティ ページ** ダイアログ ボックス。  
  
 [ベース プロジェクトのオブジェクト モデルの拡張](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 プロジェクト サブタイプがオートメーション エクステンダーを使用して、オートメーション オブジェクト モデルを拡張する方法について説明します。  
  
 [[新しい項目の追加] ダイアログ ボックスへの投稿](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)  
 項目を追加する方法について説明します、**新しい項目の追加** ダイアログ ボックス。  
  
 [プロジェクト ファイルでのデータの保存](../../extensibility/saving-data-in-project-files.md)  
 プロジェクト サブタイプが保存して、マネージ パッケージ フレームワーク (MPF) を使用して、プロジェクト ファイルのサブタイプに固有のデータを取得する方法について説明します。  
  
 [特別な展開の処理](../../extensibility/internals/handling-specialized-deployment.md)  
 実装することで、プロジェクトのサブタイプが特殊化された展開の動作を指定する方法について説明します、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>インターフェイス。  
  
 [プロパティ ページの追加と削除](../../extensibility/adding-and-removing-property-pages.md)  
 追加して、プロジェクト デザイナーのプロパティ ページの削除について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [プロジェクト タイプ](../../extensibility/internals/project-types.md)  
 詳細を示すトピックへのリンクを提供します。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プロジェクト。