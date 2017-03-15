---
title: "ソース管理プラグイン API バージョン 1.3 の新機能します。 | Microsoft Docs"
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
  - "ソース管理プラグインであり、API v1.3 の新機能"
  - "新しい [Visual Studio SDK] ソース管理プラグインとは"
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# ソース管理プラグイン API バージョン 1.3 の新機能します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ソース管理プラグイン API Version 1.3 では高度なコントロールを作成するには次の新機能を紹介します。  
  
## 変更  
 次の関数はソース管理プラグイン API Version 1.3 で追加されました :  
  
|Function|概要|  
|--------------|--------|  
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|追加機能が報告できるようにします。|  
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|ローカル ディスクでバージョン管理データベースに新しいバージョンを持つファイルをチェックできます。|  
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|指定したファイルの名前がさまざまな状態のチェック \(追加削除名前の変更リファクタリングを使用する\)|  
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|バージョン管理データベースのフォルダーとファイルをチェックできます。|  
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|バージョン管理データベースから現在のプロジェクトにファイルの指定されたリストを追加します|  
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|サイレントを 「 Get 」で指定されたファイルです \(ユーザー インターフェイスは表示されません\)|  
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|割り当てはユーザー固有オプションにアクセス|  
  
## 参照  
 [作業の開始](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)   
 [ソース管理プラグイン API バージョン 1.2 の新機能します。](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)