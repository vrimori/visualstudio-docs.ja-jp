---
title: Iactivescript::interruptscriptthread |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.InterruptScriptThread
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_InterruptScriptThread
ms.assetid: 2304d035-6d39-4811-acd3-8a9640fdbef6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d20847245e25ec6227bb043df3190a6db5f095d5
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088934"
---
# <a name="iactivescriptinterruptscriptthread"></a>IActiveScript::InterruptScriptThread
実行中のスクリプト スレッド (イベント シンク、即時実行の場合、またはマクロの呼び出し) の実行を中断します。 (たとえば、無限ループ) でスタックしているスクリプトを終了するのには、このメソッドを使用できます。 ホスト オブジェクトまたはベース以外の吹き出しでベース以外のスレッドから呼び出すことが、 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)メソッド。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT InterruptScriptThread(  
    SCRIPTTHREADID   stidThread,  // identifier of thread  
    const EXCEPINFO *pexcepinfo,  // receives error information  
    DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `stidThread`  
 [in]スレッドの中断、または、次の特殊なスレッド id の値の 1 つの識別子。  
  
|[値]|説明|  
|-----------|-------------|  
|SCRIPTTHREADID_ALL|すべてのスレッド。 割り込みは、現在進行中のすべてのスクリプト メソッドに適用されます。 呼び出し元が、スクリプトが切断されることを要求している場合を除き、次のスクリプト化されたイベントがスクリプト コードを呼び出すことでもう一度実行をによりことに注意してください、 [iactivescript::setscriptstate](../../winscript/reference/iactivescript-setscriptstate.md) SCRIPTSTATE_DISCONNECTED を持つメソッドまたはSCRIPTSTATE_INITIALIZED フラグを設定します。|  
|SCRIPTTHREADID_BASE|基本スレッドです。つまり、これで、スクリプト エンジンのスレッドがインスタンス化されました。|  
|SCRIPTTHREADID_CURRENT|現在実行中のスレッド。|  
  
 `pexcepinfo`  
 [in]アドレス、`EXCEPINFO`が中止されたスクリプトに報告されるエラー情報を含む構造体。  
  
 `dwFlags`  
 [in]関連付けられた中断時間のオプション フラグ。 次のいずれかの値を指定します。  
  
|[値]|説明|  
|-----------|-------------|  
|SCRIPTINTERRUPT_DEBUG|サポートされている場合は、現在のスクリプトの実行ポイントにあるスクリプト エンジンのデバッガーを入力します。|  
|SCRIPTINTERRUPT_RAISEEXCEPTION|スクリプト エンジンの言語のサポートをしている場合は、例外を処理するスクリプトを使用できます。 それ以外の場合、スクリプト メソッドが中断され、エラー コードは、呼び出し元に返されます。これは、イベント ソースまたはマクロの呼び出し元。|  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引数が無効です。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`E_UNEXPECTED`|呼び出しが予期されていませんでした (たとえば、スクリプト エンジンがされていないされて読み込まれるまたは初期化) します。|  
  
## <a name="see-also"></a>関連項目  
 [IActiveScript](../../winscript/reference/iactivescript.md)