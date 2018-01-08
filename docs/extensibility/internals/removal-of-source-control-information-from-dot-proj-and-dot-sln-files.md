---
title: "ソース管理情報の削除。Proj とします。Sln ファイル |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4131e3d5139911c6a1bb9b44d8d8acaefa6cb632
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>ソース管理情報の削除。Proj とします。Sln ファイル
バージョン 1.2 のソース管理プラグイン API、SCC は、情報は、MSSCCPRJ に格納されます。SCC ファイルです。 MSSCCPRJ 利点です。SCC ファイルは、SCC 情報がないソースに - .proj および .sln ファイル内にあるように、制御します。  
  
## <a name="version-12-changes"></a>バージョン 1.2 の変更  
 ソース管理プラグインで、ソース管理プラグイン API バージョン 1.1 に基づいた、ソース コントロールの概要については、プロジェクト (.proj) とソリューション (.sln) ファイルに格納されます。 AuxPath でソース管理情報のデータベースの場所を指定し、ProjName によって、データベース内で特定の場所を指定します。 この動作できます問題が発生する分岐、分岐、またはコピー操作の後に、ProjName 通常無効になります。 これらの操作の後にあるためです。  
  
 ソース管理プラグイン API 使用されているバージョン 1.1 では、IDE で ~ されているかどうか、プラグインのサポート、MSSCCPRJ を検出するために SAK ファイル。ソース管理情報を格納する SCC メソッドです。 ソース管理プラグイン API バージョン 1.2 では、MSSCCPRJ のサポートを検出するための新機能を提供します。SCC ファイルを使用せず、~ SAK ファイル。 詳細については、次を参照してください。[の排除 ~ SAK ファイル](../../extensibility/internals/elimination-of-tilde-sak-files.md)です。  
  
## <a name="see-also"></a>参照  
 [ソース管理プラグイン API バージョン 1.2 の新機能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)