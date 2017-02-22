---
title: "ファイルのステータス コードの列挙子 | Microsoft Docs"
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
  - "名前付き定数、SccStatus 列挙子"
  - "ソース管理プラグインをファイルの状態の列挙型"
  - "SccStatus 列挙子"
  - "ファイルのステータス コードの列挙子"
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# ファイルのステータス コードの列挙子
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`SccStatus` 列挙子には、ソース管理システムでファイルの状態を指定する名前付きの定数値が含まれています。 この列挙を使用、 [SccQueryInfo](../extensibility/sccqueryinfo-function.md) と `POPLISTFUNC` コールバック関数 \(を参照してください [POPLISTFUNC](../extensibility/poplistfunc.md) 詳細\)。  
  
## 構文  
  
```  
enum SccStatus {  
   SCC_STATUS_INVALID          = -1L,  
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,  
   SCC_STATUS_CONTROLLED       = 0x0001L,  
   SCC_STATUS_CHECKEDOUT       = 0x0002L,  
   SCC_STATUS_OUTOTHER         = 0x0004L,  
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,  
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,  
   SCC_STATUS_OUTOFDATE        = 0x0020L,  
   SCC_STATUS_DELETED          = 0x0040L,  
   SCC_STATUS_LOCKED           = 0x0080L,  
   SCC_STATUS_MERGED           = 0x0100L,  
   SCC_STATUS_SHARED           = 0x0200L,  
   SCC_STATUS_PINNED           = 0x0400L,  
   SCC_STATUS_MODIFIED         = 0x0800L,  
   SCC_STATUS_OUTBYUSER        = 0x1000L  
   SCC_STATUS_NOMERGE          = 0x2000L  
   SCC_STATUS_RESERVED_1       = 0x4000L  
   SCC_STATUS_RESERVED_2       = 0x8000L  
};  
```  
  
## メンバー  
 SCC\_STATUS\_INVALID  
 状態を取得できませんでした。それに依存しないでください。  
  
 SCC\_STATUS\_NOTCONTROLLED  
 ファイルはソース管理下ではありません。  
  
 SCC\_STATUS\_CONTROLLED  
 ファイルがソース管理されます。  
  
 SCC\_STATUS\_CHECKEDOUT  
 ローカル ディスク上の現在のユーザーがチェック アウトされます。  
  
 SCC\_STATUS\_OUTOTHER  
 ファイルが別のユーザーがチェック アウトします。  
  
 SCC\_STATUS\_OUTEXCLUSIVE  
 ファイルが排他的チェック アウトされています。  
  
 SCC\_STATUS\_OUTMULTIPLE  
 1 つ以上のユーザーによってファイルがチェック アウトします。  
  
 SCC\_STATUS\_OUTOFDATE  
 ファイルが最新ではありません。  
  
 SCC\_STATUS\_DELETED  
 ファイルがプロジェクトから削除されました。  
  
 SCC\_STATUS\_LOCKED  
 ファイルがロックされています。多くのバージョンが許可されます。  
  
 SCC\_STATUS\_MERGED  
 ファイルがマージされましたが、まだ修正と検証します。  
  
 SCC\_STATUS\_SHARED  
 ファイルは、プロジェクト間で共有されます。  
  
 SCC\_STATUS\_PINNED  
 ファイルは、明示的なバージョンで共有されます。  
  
 SCC\_STATUS\_MODIFIED  
 ファイルは、変更\/分割\/違反されました。  
  
 SCC\_STATUS\_OUTBYUSER  
 ファイルが、現在のユーザーがチェック アウトします。  
  
 SCC\_STATUS\_NOMERGE  
 ファイルは、決してマージすることができます、取得する前に保存する必要がありません。  
  
 SCC\_STATUS\_RESERVED\_1  
 内部使用のために予約されています。  
  
 SCC\_STATUS\_RESERVED\_2  
 内部使用のために予約されています。  
  
## 参照  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)   
 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)