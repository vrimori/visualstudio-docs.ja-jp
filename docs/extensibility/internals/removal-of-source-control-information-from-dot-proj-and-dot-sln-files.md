---
title: "ソース コントロールからの情報の削除。Proj とします。Sln ファイル | Microsoft Docs"
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
  - "ソース管理プラグイン、.sln および .proj ファイル"
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# ソース コントロールからの情報の削除。Proj とします。Sln ファイル
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ソース管理プラグイン API Version 1.2 で SCC 情報は MSSCCPRJ.SCC ファイルに格納されます。  MSSCCPRJ.SCC ファイルの利点があります SCC 情報がソース コントロールではないことです.proj .sln ファイルに変換する可能性があります。  
  
## バージョン 1.2 の変更  
 ソース管理プラグイン API のバージョン 1.1 に基づいているソース管理プラグインではソース管理に関する情報はプロジェクト \(.proj\) とソリューション ファイル \(.sln\) に格納されます。  ソース管理データベースの位置情報は AuxPath によって指定されデータベース内の特定の位置は ProjName によって指定されます。  この動作は分岐の後に ProjName がこれらの操作のいずれかの後に無効になるため問題が発生する分岐または操作をコピーできます。  
  
 ソース管理プラグイン API Version 1.1 ではプラグインがソース管理の情報を格納する MSSCCPRJ.SCC のメソッドをサポートするかどうかを確認するために ~SAK ファイルを使用します。  ソース管理プラグイン API のバージョン 1.2 は MSSCCPRJ.SCC ファイルのサポートを検出するに ~SAK ファイルを使用せずに新しい機能を提供します。  詳細については、「[削除する ~ SAK ファイル](../../extensibility/internals/elimination-of-tilde-sak-files.md)」を参照してください。  
  
## 参照  
 [ソース管理プラグイン API バージョン 1.2 の新機能します。](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)