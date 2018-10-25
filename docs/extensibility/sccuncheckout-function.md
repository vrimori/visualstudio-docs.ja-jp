---
title: SccUncheckout 関数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 79afce90f462f97d7a33a64875c4784a030f845e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49905923"
---
# <a name="sccuncheckout-function"></a>SccUncheckout 関数
この関数は、選択したファイルまたはファイルの内容をチェック アウトする前の状態に復元できるため、以前のチェック アウト操作を元に戻します。 チェック アウト後、ファイルに加えた変更は失われます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccUncheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pvContext  
 [in]ソース管理プラグイン コンテキスト構造体。  
  
 hWnd  
 [in]ソース管理プラグインが提供される任意のダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 nFiles  
 [in]指定されたファイルの数、`lpFileNames`配列。  
  
 lpFileNames  
 [in]チェック アウトを解除する対象のファイルの完全修飾パス名の配列。  
  
 方法は限られて  
 [in]コマンドのフラグ (未使用)。  
  
 pvOptions  
 [in]ソース管理プラグインに固有のオプション。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|チェック アウトの取り消しに成功しました。|  
|SCC_E_FILENOTCONTROLLED|選択したファイルはソース コード管理下ではありません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題の可能性へのアクセスに問題が発生しました。 再試行をお勧めします。|  
|SCC_E_NONSPECIFICERROR|不特定のエラーです。 元に戻すチェック アウトは成功しませんでした。|  
|SCC_E_NOTCHECKEDOUT|ユーザーのファイルをチェック アウトではありません。|  
|SCC_E_NOTAUTHORIZED|この操作を実行できません。|  
|SCC_E_PROJNOTOPEN|ソース管理からプロジェクトが開かれていません。|  
|SCC_I_OPERATIONCANCELED|操作が完了する前に取り消されました。|  
  
## <a name="remarks"></a>Remarks  
 この操作の後、`SCC_STATUS_CHECKEDOUT`と`SCC_STATUS_MODIFIED`フラグはどちらもクリアされますファイルをチェック アウトの取り消しが実行されました。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)