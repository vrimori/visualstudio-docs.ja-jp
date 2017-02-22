---
title: "オートメーション モデルに貢献しています。 | Microsoft Docs"
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
  - "オートメーション [Visual Studio SDK]"
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# オートメーション モデルに貢献しています。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio には、環境をカスタマイズするための一連のオートメーション インターフェイスが用意されています。 オートメーション モデルは、エンドユーザーが Visual Studio のアドインおよび拡張機能を作成することができるオブジェクト モデルです。  
  
 さらの適切では、VSPackage 開発者は、オートメーション モデルに投稿するにはこれにより、アドインを作成し、一般に、一貫性のあるユーザー エクスペリエンスを提供モデルで、VSPackage を使用するときに、VSPackage のエンドユーザーを有効に [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。  
  
 エンドユーザーのエクスペリエンスを一貫したするためには、行うことができる一連のガイドライン、VSPackage のオートメーション モデルでアイデアに依存するように、VSPackage を設計する際 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。  
  
## このセクションの内容  
 [オートメーション モデルの概要](../../extensibility/internals/automation-model-overview.md)  
 関連の一般的な環境の主要な側面を制御するオブジェクトのグループには、オートメーション モデルを定義します。 この一連のオブジェクトは、オートメーション モデルの図で示しています。  
  
 [Vspackage のための自動化を提供します。](../../extensibility/internals/providing-automation-for-vspackages.md)  
 VSPackage のための自動化を提供する 2 つの主な方法について説明します。  
  
 [プロジェクト オブジェクトを公開します。](../../extensibility/internals/exposing-project-objects.md)  
 VSPackage に固有のオブジェクトを作成するための手順を説明します。  
  
 [プロジェクトのモデリング](../../extensibility/internals/project-modeling.md)  
 新しいプロジェクトの種類の自動化を作成するために必要な標準的なプロジェクトのオブジェクトについて説明し、プロジェクトの自動化に続くパスを示します。 このトピックでは、宣言とクラスの実装の一覧も示します。  
  
 [イベントを公開します。](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 オートメーション モデルのイベントを作成するための手順を説明します。  
  
 [オートメーション \[オプション\] ページのサポート](../Topic/Automation%20Support%20for%20Options%20Pages.md)  
 カスタムの VSPackage のプロパティをサポートするために、オートメーション オブジェクトを返す方法について説明 **オプション** \] ダイアログ ボックスで、 **ツール** メニューを拡張することによって、 `DTE.Properties` オブジェクトです。  
  
 [コードのための自動化を提供します。](../../extensibility/internals/providing-automation-for-code.md)  
 コードのオートメーション モデルを作成する必要がないことについて説明します。 ただし、リンクは、コード モデルにわかりやすい情報を提供するこのトピックでは提供されます。  
  
 [方法: Windows 用の自動化](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 オートメーションを提供することがあることをお勧めオートメーション オブジェクトをウィンドウで使用できるようにして、環境が既製のオートメーション オブジェクトを既に提供していない場合について説明します。 ツール ウィンドウとドキュメント ウィンドウのための自動化について説明します。  
  
 [オートメーション モデルを使用します。](../../extensibility/internals/using-the-automation-model.md)  
 オートメーション コンシューマーを取得する方法、初期のプロジェクト オートメーション オブジェクトを示す 2 つのコード例を提供します。  
  
 [構成および SelectedItem オブジェクトのための自動化](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 構成オプションのための自動化と選択した項目のための自動化についてを説明します。  
  
## 関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 DTE オートメーション オブジェクト モデルでは、VSPackage が参加する方法を示すコード サンプルを提供します。 パラメーター、戻り値、および選択した注釈の一覧です。  
  
## 関連項目