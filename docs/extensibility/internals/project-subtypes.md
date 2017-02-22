---
title: "プロジェクトのサブタイプ | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロジェクト [Visual Studio SDK] サブタイプ"
  - "プロジェクトのサブタイプ [Visual Studio SDK]"
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# プロジェクトのサブタイプ
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

プロジェクトのサブタイプを使用すると、flavor のプロジェクト システムの動作をカスタマイズまたは [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 カスタマイズ内の項目をフィルター処理を追加またはプロジェクト ファイルで追加のデータの保存が可能です、 **新しい項目の追加** ダイアログ ボックスで、アセンブリのデバッグおよび展開する方法を制御し、プロジェクトを拡張する **プロパティ ページ** \] ダイアログ ボックス。 Vspackage では、COM の集計を使用してプロジェクトのサブタイプを実装します。  
  
> [!NOTE]
>  Visual C プロジェクト システムは、プロジェクトのサブタイプをサポートしていません。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 自体は、プロジェクトのサブタイプを使用して、SQL Server とスマート デバイス プロジェクトを実装します。  
  
## このセクションの内容  
 [プロジェクトのサブタイプの設計](../../extensibility/internals/project-subtypes-design.md)  
 プロジェクトのサブタイプの概念について説明します。  
  
 [プロジェクトのサブタイプの初期化シーケンス](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 によってプログラムによるプロジェクトのサブタイプの初期化シーケンスが記述される [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 環境です。  
  
 [プロパティとプロジェクトのサブタイプによって拡張メソッド](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 機能とプロジェクトのサブタイプを使用して、最も頻繁に拡張メソッドの詳細な説明を示します。  
  
 [MSBuild プロジェクト ファイルでデータを保持します。](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 プロジェクト ファイル内のデータを永続化する方法と使用方法について説明 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> プロジェクト サブタイプ集計レベル間でプロジェクト ファイル内のデータを維持します。  
  
 [プロジェクト プロパティのユーザー インターフェイス](../../extensibility/internals/project-property-user-interface.md)  
 プロジェクトのサブタイプが、プロジェクトを変更する方法について説明 **プロパティ ページ** \] ダイアログ ボックス。  
  
 [ベースのプロジェクトのオブジェクト モデルの拡張](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 プロジェクトのサブタイプがオートメーション エクステンダーを使用して、オートメーション オブジェクト モデルを拡張する方法について説明します。  
  
 [原因となっている、新しい項目\] ダイアログ ボックスを追加](../Topic/Contributing%20to%20the%20Add%20New%20Item%20Dialog%20Box.md)  
 項目を追加する方法について説明します **新しい項目の追加** \] ダイアログ ボックス。  
  
 [プロジェクト ファイル内のデータを保存](../../extensibility/saving-data-in-project-files.md)  
 プロジェクトのサブタイプの保存および管理されているパッケージ フレームワーク \(MPF\) を使用して、プロジェクト ファイルのサブタイプに固有のデータを取得する方法について説明します。  
  
 [処理に特化した展開](../../extensibility/internals/handling-specialized-deployment.md)  
 実装することで、プロジェクトのサブタイプが特殊な配置の動作を指定する方法について説明します <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> インターフェイスです。  
  
 [追加して、プロパティ ページを削除します。](../../extensibility/adding-and-removing-property-pages.md)  
 追加して、プロジェクト デザイナーのプロパティ ページを削除について説明します。  
  
## 関連項目  
 [プロジェクトの種類](../../extensibility/internals/project-types.md)  
 詳細を示すトピックへのリンクを提供 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] プロジェクトです。