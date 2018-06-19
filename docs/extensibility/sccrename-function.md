---
title: SccRename 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c24d84ff659d287f3b32be2b5585ded16b148395
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137805"
---
# <a name="sccrename-function"></a>SccRename 関数
この関数は、ソース管理システムでファイルを変更します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccRename(  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName,  
   LPCSTR lpNewName  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pvContext  
 [in]ソース管理プラグイン コンテキスト構造体。  
  
 hWnd  
 [in]ソース管理プラグインで提供されるダイアログ ボックスをすべての親として使用できる IDE ウィンドウへのハンドル。  
  
 lpFileName  
 [in]名前が変更されるファイルの完全修飾ファイル名。  
  
 lpNewName  
 [in]完全修飾の新しい名前。 ディレクトリ パスが異なる場合は、し、ファイルが 1 つのサブディレクトリからに移動別です。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|名前変更操作が正常に完了しました。|  
|SCC_E_PROJNOTOPEN|プロジェクトは、ソース管理下で開かれていません。|  
|SCC_E_FILENOTCONTROLLED|ファイルはソース管理されません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークや競合の問題の可能性があるためのアクセスに関する問題が発生しました。|  
|SCC_E_NOTAUTHORIZED|ユーザーは、この操作を実行する権限がありません。|  
|SCC_E_COULDNOTCREATEPROJECT|名前の変更プロセスの一部として、プロジェクトを作成できませんでした。|  
|SCC_E_OPNOTPERFORMED|操作は実行されませんでした。|  
|SCC_E_NONSPECIFICERROR|指定されていないか、一般的なエラーが発生しました。|  
  
## <a name="remarks"></a>コメント  
 この関数は、ファイル名を変更または移動する、1 つの場所から別に、ソース管理システムで使用できます。 ソース管理プラグインは、ディスク上のファイルへのアクセスはされません。 ローカル ファイルの名前を変更する、IDE の責任です。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)