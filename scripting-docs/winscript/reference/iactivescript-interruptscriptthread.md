---
title: "IActiveScript::InterruptScriptThread |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.InterruptScriptThread
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_InterruptScriptThread
ms.assetid: 2304d035-6d39-4811-acd3-8a9640fdbef6
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad717ee950dda4f0f0d7a14292f0f5f150ab4973
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptinterruptscriptthread"></a>IActiveScript::InterruptScriptThread
実行中のスクリプト スレッド (イベント シンク、即時実行の場合、またはマクロの呼び出し) の実行を中断します。 このメソッドは、(たとえば、無限ループ) に残っているスクリプトを終了するのには使用できます。 ホスト オブジェクトまたはベース以外吹き出しの結果として得られることがなくベース以外のスレッドから呼び出すことが、 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT InterruptScriptThread(  
    SCRIPTTHREADID   stidThread,  // identifier of thread  
    const EXCEPINFO *pexcepinfo,  // receives error information  
    DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `stidThread`  
 [in]スレッドの中断、または、次の特殊なスレッド識別子の値の 1 つの識別子。  
  
|値|説明|  
|-----------|-------------|  
|SCRIPTTHREADID_ALL|すべてのスレッド。 割り込みは、現在進行中のすべてのスクリプト メソッドに適用されます。 呼び出し元が、スクリプトが切断されることを要求している場合を除き、次のスクリプト化されたイベントによって、スクリプト コードを呼び出して、再度実行するに注意してください、 [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) SCRIPTSTATE_DISCONNECTED を持つメソッドまたはSCRIPTSTATE_INITIALIZED フラグを設定します。|  
|SCRIPTTHREADID_BASE|基本スレッドです。つまりをスクリプト エンジンのスレッドがインスタンス化されます。|  
|SCRIPTTHREADID_CURRENT|現在実行中のスレッド。|  
  
 `pexcepinfo`  
 [in]アドレス、`EXCEPINFO`が中止されたスクリプトに報告されるエラー情報を含む構造体。  
  
 `dwFlags`  
 [in]中断に関連付けられているオプションのフラグです。 次のいずれかの値を指定します。  
  
|値|説明|  
|-----------|-------------|  
|SCRIPTINTERRUPT_DEBUG|サポートされている場合は、現在のスクリプト実行ポイントで、スクリプト エンジンのデバッガーを入力します。|  
|SCRIPTINTERRUPT_RAISEEXCEPTION|スクリプト エンジンの言語でサポートされている場合は、例外を処理するスクリプトを使用できます。 それ以外の場合、スクリプト メソッドが中断され、エラー コードは、呼び出し元に返されます。つまり、イベント ソースまたはマクロ呼び出し元は、します。|  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引数が無効です。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`E_UNEXPECTED`|呼び出しが予期されていませんでした (たとえば、スクリプト エンジンがされていないされて読み込まれたまたは初期化) します。|  
  
## <a name="see-also"></a>関連項目  
 [IActiveScript](../../winscript/reference/iactivescript.md)