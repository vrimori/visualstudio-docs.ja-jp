---
title: ソース管理情報の削除。Proj とします。Sln ファイル |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 695a4ccfc5da20bda25c78929488625c244959a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128988"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>ソース管理情報の削除。Proj とします。Sln ファイル
バージョン 1.2 のソース管理プラグイン API、SCC は、情報は、MSSCCPRJ に格納されます。SCC ファイルです。 MSSCCPRJ 利点です。SCC ファイルは、SCC 情報がないソースに - .proj および .sln ファイル内にあるように、制御します。  
  
## <a name="version-12-changes"></a>バージョン 1.2 の変更  
 ソース管理プラグインで、ソース管理プラグイン API バージョン 1.1 に基づいた、ソース コントロールの概要については、プロジェクト (.proj) とソリューション (.sln) ファイルに格納されます。 AuxPath でソース管理情報のデータベースの場所を指定し、ProjName によって、データベース内で特定の場所を指定します。 この動作できます問題が発生する分岐、分岐、またはコピー操作の後に、ProjName 通常無効になります。 これらの操作の後にあるためです。  
  
 ソース管理プラグイン API 使用されているバージョン 1.1 では、IDE で ~ されているかどうか、プラグインのサポート、MSSCCPRJ を検出するために SAK ファイル。ソース管理情報を格納する SCC メソッドです。 ソース管理プラグイン API バージョン 1.2 では、MSSCCPRJ のサポートを検出するための新機能を提供します。SCC ファイルを使用せず、~ SAK ファイル。 詳細については、次を参照してください。[の排除 ~ SAK ファイル](../../extensibility/internals/elimination-of-tilde-sak-files.md)です。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API バージョン 1.2 の新機能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)