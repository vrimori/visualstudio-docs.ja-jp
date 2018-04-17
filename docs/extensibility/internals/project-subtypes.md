---
title: プロジェクトのサブタイプ |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e91a16ad11f7089230138919519922d58f3cc472
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="project-subtypes"></a>プロジェクトのサブタイプ
プロジェクトのサブタイプでは、カスタマイズしたりのプロジェクト システムの動作を flavor[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 カスタマイズには、プロジェクト ファイルを追加または内の項目をフィルター処理で追加のデータを保存、**新しい項目の追加**ダイアログ ボックスで、アセンブリのデバッグし、配置方法を制御して、プロジェクトの拡張**プロパティページ** ダイアログ ボックス。 Vspackage では、COM の集計を使用してプロジェクトのサブタイプを実装します。  
  
> [!NOTE]
>  Visual C プロジェクト システムは、プロジェクトのサブタイプをサポートしていません。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 自体は、プロジェクトのサブタイプを使用して、SQL Server およびスマート デバイス プロジェクトを実装します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [プロジェクト サブタイプのデザイン](../../extensibility/internals/project-subtypes-design.md)  
 プロジェクトのサブタイプの概念について説明します。  
  
 [プロジェクト サブタイプの初期化シーケンス](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 によってプログラムでのプロジェクト サブタイプの初期化シーケンスが記述[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境。  
  
 [プロジェクト サブタイプによって拡張されるプロパティとメソッド](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 機能とプロジェクトのサブタイプを使用して、最も頻繁に拡張メソッドの詳細な説明を提供します。  
  
 [MSBuild プロジェクト ファイルでのデータの保持](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 プロジェクト ファイル内のデータを永続化する方法と使用方法について説明します<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>プロジェクト サブタイプ集計レベルで、プロジェクト ファイル内のデータを維持するためにします。  
  
 [プロジェクト プロパティのユーザー インターフェイス](../../extensibility/internals/project-property-user-interface.md)  
 プロジェクトのサブタイプがプロジェクトを変更する方法について説明**プロパティ ページ** ダイアログ ボックス。  
  
 [ベース プロジェクトのオブジェクト モデルの拡張](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 プロジェクトのサブタイプがオートメーション エクステンダーを使用して、オートメーション オブジェクト モデルを拡張する方法について説明します。  
  
 [[新しい項目の追加] ダイアログ ボックスへの投稿](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)  
 項目を追加する方法について説明、**新しい項目の追加** ダイアログ ボックス。  
  
 [プロジェクト ファイルでのデータの保存](../../extensibility/saving-data-in-project-files.md)  
 プロジェクトのサブタイプが保存し、Managed Package Framework (MPF) を使用して、プロジェクト ファイル内のサブタイプに固有のデータを取得する方法について説明します。  
  
 [特別な展開の処理](../../extensibility/internals/handling-specialized-deployment.md)  
 実装することで、プロジェクトのサブタイプが特殊な展開の動作を指定する方法について説明します、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>インターフェイスです。  
  
 [プロパティ ページの追加と削除](../../extensibility/adding-and-removing-property-pages.md)  
 追加して、プロジェクト デザイナーのプロパティ ページを削除するについて説明します。  
  
## <a name="related-sections"></a>関連項目  
 [プロジェクト タイプ](../../extensibility/internals/project-types.md)  
 詳細を示すトピックへのリンクを提供[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プロジェクト。