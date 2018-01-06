---
title: "ファイルのステータス コード列挙子 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7957a8b841c34b85983af1aa152af466c469f8e1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="file-status-code-enumerator"></a>ファイルのステータス コード列挙子
`SccStatus`列挙子には、ソース管理システムでファイルの状態を指定する名前付きの定数値が含まれています。 この列挙を使用、 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)と`POPLISTFUNC`コールバック関数 (を参照してください[POPLISTFUNC](../extensibility/poplistfunc.md)詳細)。  
  
## <a name="syntax"></a>構文  
  
```  
enum SccStatus {  
   SCC_STATUS_INVALID          = -1L,  
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,  
   SCC_STATUS_CONTROLLED       = 0x0001L,  
   SCC_STATUS_CHECKEDOUT       = 0x0002L,  
   SCC_STATUS_OUTOTHER         = 0x0004L,  
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,  
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,  
   SCC_STATUS_OUTOFDATE        = 0x0020L,  
   SCC_STATUS_DELETED          = 0x0040L,  
   SCC_STATUS_LOCKED           = 0x0080L,  
   SCC_STATUS_MERGED           = 0x0100L,  
   SCC_STATUS_SHARED           = 0x0200L,  
   SCC_STATUS_PINNED           = 0x0400L,  
   SCC_STATUS_MODIFIED         = 0x0800L,  
   SCC_STATUS_OUTBYUSER        = 0x1000L  
   SCC_STATUS_NOMERGE          = 0x2000L  
   SCC_STATUS_RESERVED_1       = 0x4000L  
   SCC_STATUS_RESERVED_2       = 0x8000L  
};  
```  
  
## <a name="members"></a>メンバー  
 SCC_STATUS_INVALID  
 状態を取得できませんでした。それに依存しないでください。  
  
 SCC_STATUS_NOTCONTROLLED  
 ファイルはソース管理下ではありません。  
  
 SCC_STATUS_CONTROLLED  
 ファイルは、ソース管理下にあること。  
  
 SCC_STATUS_CHECKEDOUT  
 ローカル ディスク上の現在のユーザーによってチェック アウトをされています。  
  
 SCC_STATUS_OUTOTHER  
 ファイルは別のユーザーによってチェック アウトをされています。  
  
 SCC_STATUS_OUTEXCLUSIVE  
 ファイルが排他的チェック アウトされています。  
  
 SCC_STATUS_OUTMULTIPLE  
 ファイルは 1 つ以上のユーザーによってチェック アウトをされています。  
  
 SCC_STATUS_OUTOFDATE  
 ファイルが最新ではありません。  
  
 SCC_STATUS_DELETED  
 ファイルがプロジェクトから削除されました。  
  
 SCC_STATUS_LOCKED  
 ファイルがロックされています。多くのバージョンが許可されます。  
  
 SCC_STATUS_MERGED  
 ファイルがマージされましたが、まだ固定/検証します。  
  
 SCC_STATUS_SHARED  
 ファイルは、プロジェクト間で共有されます。  
  
 SCC_STATUS_PINNED  
 ファイルは、明示的なバージョンで共有されます。  
  
 SCC_STATUS_MODIFIED  
 ファイルは、変更/切断/に違反しました。  
  
 SCC_STATUS_OUTBYUSER  
 ファイルは現在のユーザーによってチェック アウトをされています。  
  
 SCC_STATUS_NOMERGE  
 ファイルは、しないでマージすることができます、取得する前に未保存必要があります。  
  
 SCC_STATUS_RESERVED_1  
 内部使用のために予約されています。  
  
 SCC_STATUS_RESERVED_2  
 内部使用のために予約されています。  
  
## <a name="see-also"></a>参照  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)   
 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)