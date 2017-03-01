---
title: "ディレクトリの状態コードの列挙子 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 9cee432270a31eacbcbd09d80d861aadbf7bc3f2
ms.lasthandoff: 02/22/2017

---
# <a name="directory-status-code-enumerator"></a>ディレクトリの状態コードの列挙子
`SccDirStatus`列挙子には、ソース管理システムのディレクトリの状態を指定する名前付き定数の値が含まれています。 この列挙体を使って、 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)します。 これは、ソース コントロールのプラグイン API のバージョン 1.2 で導入されました。  
  
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
 ディレクトリは、ソース管理下ではありません。  
  
 SCC_DIRSTATUS_CONTROLLED  
 ディレクトリでは、ソース管理の対象です。  
  
 SCC_DIRSTATUS_EMPTYPROJ  
 このディレクトリに対応するプロジェクトが空です。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)   
 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
