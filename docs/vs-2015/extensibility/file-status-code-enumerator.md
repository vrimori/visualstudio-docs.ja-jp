---
title: 状態コードの列挙子のファイル |Microsoft Docs
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
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 18e8b61c16b3a49d19b7571d529af633f6074d48
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49268386"
---
# <a name="file-status-code-enumerator"></a>ファイルのステータス コードの列挙子
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`SccStatus`列挙子には、ソース管理システムでファイルの状態を指定する名前付き定数の値が含まれています。 この列挙体を使って、 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)と`POPLISTFUNC`コールバック関数 (を参照してください[POPLISTFUNC](../extensibility/poplistfunc.md)詳細については)。  
  
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
 ファイルはソース管理です。  
  
 SCC_STATUS_CHECKEDOUT  
 ローカル ディスク上の現在のユーザーによってチェック アウトします。  
  
 SCC_STATUS_OUTOTHER  
 ファイルが別のユーザーによってチェック アウトします。  
  
 SCC_STATUS_OUTEXCLUSIVE  
 ファイルが排他的チェック アウトします。  
  
 SCC_STATUS_OUTMULTIPLE  
 ファイルが 1 つ以上のユーザーによってチェック アウトします。  
  
 SCC_STATUS_OUTOFDATE  
 ファイルが最新ではありません。  
  
 SCC_STATUS_DELETED  
 ファイルがプロジェクトから削除されました。  
  
 SCC_STATUS_LOCKED  
 ファイルがロックされています。その他のバージョンが許可されています。  
  
 SCC_STATUS_MERGED  
 ファイルがマージされましたが、まだ固定/検証済み。  
  
 SCC_STATUS_SHARED  
 ファイルは、プロジェクト間で共有されます。  
  
 SCC_STATUS_PINNED  
 ファイルは、特定のバージョンで共有されます。  
  
 SCC_STATUS_MODIFIED  
 ファイルを変更/分割/違反とされました。  
  
 SCC_STATUS_OUTBYUSER  
 現在のユーザーによってファイルがチェック アウトします。  
  
 SCC_STATUS_NOMERGE  
 ファイルにマージできることはありません、取得する前に未保存必要があります。  
  
 SCC_STATUS_RESERVED_1  
 内部使用のために予約されています。  
  
 SCC_STATUS_RESERVED_2  
 内部使用のために予約されています。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)   
 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)

