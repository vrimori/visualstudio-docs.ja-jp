---
title: ソース管理情報の削除。Proj とします。Sln ファイル |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 850f2278480b27eb302fe9cc87c608c0cd522e38
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761536"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>.Proj および .Sln ファイルからのソース管理情報の削除
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

ソース管理プラグイン API、SCC のバージョン 1.2 では、情報は、MSSCCPRJ に格納されます。SCC ファイルです。 MSSCCPRJ 利点です。SCC ファイルでは、SCC 情報をしないソースして-.proj および .sln ファイルでは、制御します。  
  
## <a name="version-12-changes"></a>バージョン 1.2 の変更  
 ソース管理プラグインのソース管理プラグイン API バージョン 1.1 に基づく、ソース管理については、プロジェクト (.proj) とソリューション (.sln) ファイルに格納されます。 AuxPath でソース管理情報のデータベースの場所が指定され、ProjName で、データベース内の特定の場所を指定します。 ProjName は通常はできないため、有効なこれらの操作の後にこの動作分岐、フォーク、またはコピー操作の後に問題が発生できます。  
  
 ソース管理プラグイン API バージョン 1.1 では、IDE の使用で ~ SAK ファイル、プラグインのサポート、MSSCCPRJ かどうかを検出します。ソース管理の情報を格納する SCC メソッド。 ソース管理プラグイン API バージョン 1.2 では、MSSCCPRJ のサポートを検出するための新しい機能を提供します。SCC ファイルを使用せず、~ SAK ファイル。 詳細については、次を参照してください。[の排除 ~ SAK ファイル](../../extensibility/internals/elimination-of-tilde-sak-files.md)します。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API バージョン 1.2 の新機能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

