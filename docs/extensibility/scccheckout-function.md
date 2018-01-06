---
title: "SccCheckout 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccCheckout
helpviewer_keywords: SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: af8aac642ecd21f8f4709874e4e3e6ff0b3e58b5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="scccheckout-function"></a>SccCheckout 関数
完全修飾ファイル名のリストを指定するには、この関数はそれらローカル ドライブにします。 コメントは、チェック アウトされているすべてのファイルに適用されます。コメントの引数を指定できます、`null`文字列。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccCheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
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
 [in]チェック アウトを選択したファイルの数。  
  
 lpFileNames  
 [in]ファイルをチェック アウトの完全修飾のローカル パス名の配列。  
  
 lpComment  
 [in]各チェック アウトされている選択したファイルに適用されるコメントです。  
  
 foptions の   
 [in]コマンドのフラグ (を参照してください[ビットフラグが特定のコマンドで使用される](../extensibility/bitflags-used-by-specific-commands.md))。  
  
 pvOptions  
 [in]ソース管理プラグインに固有のオプションです。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|チェック アウトは成功しました。|  
|SCC_E_FILENOTCONTROLLED|選択したファイルはソース コード管理下ではありません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークや競合の問題の可能性があるためのアクセスに関する問題が発生しました。 再試行することをお勧めします。|  
|SCC_E_NOTAUTHORIZED|この操作を実行するユーザーが許可されていません。|  
|SCC_E_NONSPECIFICERROR|不特定のエラーです。 ファイル チェック アウトされませんでした。|  
|SCC_E_ALREADYCHECKEDOUT|ユーザーでは、ファイルをチェック アウトが既に存在します。|  
|SCC_E_FILEISLOCKED|ファイルがロックされている、新しいバージョンの作成を禁止することです。|  
|SCC_E_FILEOUTEXCLUSIVE|別のユーザーには、このファイルで排他チェック アウトが行われます。|  
|SCC_I_OPERATIONCANCELED|操作が完了する前に取り消されました。|  
  
## <a name="see-also"></a>参照  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [特定のコマンドで使用されるビットフラグ](../extensibility/bitflags-used-by-specific-commands.md)