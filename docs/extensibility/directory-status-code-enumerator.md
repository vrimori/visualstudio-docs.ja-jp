---
title: ディレクトリのステータス コード列挙子 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 539dc4c2ea7b33ce88465f1d8f6651dc890c8e45
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="directory-status-code-enumerator"></a>ディレクトリのステータス コード列挙子
`SccDirStatus`列挙子には、ソース管理システムのディレクトリの状態を指定する名前付きの定数値が含まれています。 この列挙体を使って、 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)です。 これは、ソース管理プラグイン API のバージョン 1.2 で導入されました。  
  
## <a name="syntax"></a>構文  
  
```  
enum SccDirStatus {  
   SCC_DIRSTATUS_INVALID       = -1L,  
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,  
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,  
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L  
};  
```  
  
## <a name="members"></a>メンバー  
 SCC_DIRSTATUS_INVALID  
 状態を取得できませんでした。それに依存しないでください。  
  
 SCC_DIRSTATUS_NOTCONTROLLED  
 ディレクトリがソース管理下ではありません。  
  
 SCC_DIRSTATUS_CONTROLLED  
 ディレクトリは、ソース管理下にあること。  
  
 SCC_DIRSTATUS_EMPTYPROJ  
 このディレクトリに対応するプロジェクトが空です。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)   
 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)