---
title: "ソース管理の統合 Essentials | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ソース管理の統合、essentials"
  - "ソース管理の統合, 概要"
  - "essentials、ソース管理の統合"
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# ソース管理の統合 Essentials
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

サポート [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のソース管理の統合の 2 種類 : 基本機能を提供しソース管理プラグイン API を使用してビルド ソース管理プラグイン以前の API \(MSSCCI\)より信頼性の高い機能を提供する VSPackage ベースのソース管理の統合のソリューション。  
  
## ソース管理プラグイン  
 ソース管理プラグインはソース管理プラグイン API を実装する DLL として作成されます。  登録とソース管理システムの統合機能はAPI が提供されます。  この方法を実行しソース管理や VSPackage よりほとんどのソース管理操作に [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の \(UI\) ユーザー インターフェイスを使用します。  
  
 ソース管理プラグイン API を使用してソース管理プラグインを実行するには次の手順を実行する :  
  
1.  [ソース管理プラグイン](../../extensibility/source-control-plug-ins.md) に指定された関数を実装する DLL を作成します。  
  
2.  [方法: ソース管理プラグインのインストール](../../extensibility/internals/how-to-install-a-source-control-plug-in.md) に説明されているように適切なレジストリ エントリを作成して DLL を登録します。  
  
3.  ソース管理のアダプターのパッケージを求められたらヘルパーの UI を作成し表示します \(その [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のコンポーネントはソース管理のプラグインを使用してソース管理機能を処理します\)。  
  
 詳細については、「[ソース管理プラグインの作成](../../extensibility/internals/creating-a-source-control-plug-in.md)」を参照してください。  
  
## ソース管理 VSPackage  
 ソース管理の VSPackage の実装の割り当て [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のソース管理の UI のカスタマイズされた置換を作成できます。  この方法はソース管理の統合の詳細に制御しますがUI 要素を提供しプラグインで別の方法で提供されるソース管理インターフェイスを実装する必要があります。  
  
 ソース管理 VSPackage を実行するには次の操作が必要です :  
  
1.  [登録と選択](../../extensibility/internals/registration-and-selection-source-control-vspackage.md) に説明されているように独自のソース管理 VSPackage を作成および登録します。  
  
2.  カスタム UI と既定のソース コントロールの UI を置き換えます。  「[カスタム ユーザー インターフェイス](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)」を参照してください。  
  
3.  使用するグリフを指定し  **ソリューション エクスプローラー**  グリフのイベントを処理します。  「[グリフ コントロール](../../extensibility/internals/glyph-control-source-control-vspackage.md)」を参照してください。  
  
4.  ハンドル クエリの編集やクエリが [クエリを保存クエリの編集](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md) に示すようにイベントを格納します。  
  
 詳細については、「[ソース コントロール VSPackage を作成します。](../../extensibility/internals/creating-a-source-control-vspackage.md)」を参照してください。  
  
## 参照  
 [概要](../../extensibility/internals/source-control-integration-overview.md)   
 [ソース管理プラグインの作成](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [ソース コントロール VSPackage を作成します。](../../extensibility/internals/creating-a-source-control-vspackage.md)