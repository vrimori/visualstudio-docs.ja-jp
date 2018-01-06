---
title: "SccUncheckout 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccUncheckout
helpviewer_keywords: SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f9b4b2f06b8ee020ca07e780836ec2abbbc96e82
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="sccuncheckout-function"></a>SccUncheckout 関数
この関数には、選択したファイルまたはファイルの内容をチェック アウト前の状態に復元できるため、前のチェック アウト操作が元に戻します。 チェック アウト後ファイルに加えられたすべての変更は失われます。  
  
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
 [in]ソース管理プラグインで提供されるダイアログ ボックスをすべての親として使用できる IDE ウィンドウへのハンドル。  
  
 nFiles  
 [in]指定されたファイルの数、`lpFileNames`配列。  
  
 lpFileNames  
 [in]チェック アウトを解除する対象のファイルの完全修飾のローカル パス名の配列。  
  
 foptions の   
 [in]コマンド フラグ (使用しない) です。  
  
 pvOptions  
 [in]ソース管理プラグインに固有のオプションです。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|チェック アウトの取り消しが正常に完了しました。|  
|SCC_E_FILENOTCONTROLLED|選択したファイルはソース コード管理下ではありません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークや競合の問題の可能性があるためのアクセスに関する問題が発生しました。 再試行することをお勧めします。|  
|SCC_E_NONSPECIFICERROR|不特定のエラーです。 元に戻すチェック アウトは成功しませんでした。|  
|SCC_E_NOTCHECKEDOUT|ユーザーには、ファイルをチェック アウトはありません。|  
|SCC_E_NOTAUTHORIZED|この操作を実行するユーザーが許可されていません。|  
|SCC_E_PROJNOTOPEN|ソース管理からプロジェクトが開かれていません。|  
|SCC_I_OPERATIONCANCELED|操作が完了する前に取り消されました。|  
  
## <a name="remarks"></a>コメント  
 この操作の後、`SCC_STATUS_CHECKEDOUT`と`SCC_STATUS_MODIFIED`フラグはどちらもクリアされますチェック アウトの取り消しが実行されたファイルです。  
  
## <a name="see-also"></a>参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)