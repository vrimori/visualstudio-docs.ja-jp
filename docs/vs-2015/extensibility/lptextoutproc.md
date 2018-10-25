---
title: LPTEXTOUTPROC |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 37fe822a60e2f4b9628c66d9e4d292e5bc814668
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49925566"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ユーザーは、統合開発環境 (IDE) 内からソース管理操作を実行するとき、ソース管理プラグインは、操作に関連するエラーまたは状態のメッセージを伝達するためにする可能性があります。 プラグインはできますこの目的の表示の独自のメッセージ ボックス。 ただし、詳細のシームレスな統合をプラグインできる文字列に渡す、IDE では、状態情報を表示することをネイティブで表示されます。 このメカニズムは、`LPTEXTOUTPROC`関数ポインター。 IDE では、エラーと状態を表示するため (詳細については、以下で説明) この関数を実装します。  
  
 IDE をソース管理プラグインをこの関数に関数ポインターとして渡す、`lpTextOutProc`を呼び出すときに、パラメーター、 [SccOpenProject](../extensibility/sccopenproject-function.md)します。 呼び出しの途中での例については、SCC 操作中に、 [SccGet](../extensibility/sccget-function.md)多数のファイルを含む、プラグイン、呼び出すことができます、`LPTEXTOUTPROC`関数を定期的に表示する文字列を渡します。 IDE は、または個別のメッセージ ボックスで、必要に応じて、出力ウィンドウにステータス バーの これらの文字列を表示する場合があります。 必要に応じて、IDE が持つ特定のメッセージを表示することができます、**キャンセル**ボタンをクリックします。 これにより、ユーザー、操作をキャンセルして、IDE をプラグインにこの情報を渡す機能を提供します。  
  
## <a name="signature"></a>署名  
 IDE には、関数は、次のシグネチャの出力します。  
  
```cpp#  
typedef LONG (*LPTEXTOUTPROC) (  
   LPSTR display_string,  
   LONG mesg_type  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 display_string  
 表示するテキスト文字列。 この文字列は、キャリッジ リターン、ライン フィードでない終了する必要があります。  
  
 mesg_type  
 メッセージの種類。 次の表では、このパラメーターのサポートされている値を示します。  
  
|[値]|説明|  
|-----------|-----------------|  
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|メッセージは情報、警告、またはエラーと見なされます。|  
|`SCC_MSG_STATUS`|メッセージは、状態が表示され、ステータス バーに表示されることができます。|  
|`SCC_MSG_DOCANCEL`|メッセージ文字列なしで送信されます。|  
|`SCC_MSG_STARTCANCEL`|表示の開始、**キャンセル**ボタンをクリックします。|  
|`SCC_MSG_STOPCANCEL`|表示を停止、**キャンセル**ボタンをクリックします。|  
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|バック グラウンド操作をキャンセルできるが IDE の確認: IDE を返します`SCC_MSG_RTN_CANCEL`操作がキャンセルされた場合を返しますそれ以外の場合、`SCC_MSG_RTN_OK`します。 `display_string`としてパラメーターをキャストする[SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled)構造体は、ソース管理プラグインによって提供されます。|  
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|バージョン コントロールから取得される前に、ファイルについて、IDE を指示します。 `display_string`としてパラメーターをキャストする[SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile)構造体は、ソース管理プラグインによって提供されます。|  
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|バージョン コントロールから取得された後、ファイルについて、IDE を指示します。 `display_string`としてパラメーターをキャストする[SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile)構造体は、ソース管理プラグインによって提供されます。|  
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|バック グラウンド操作の現在の状態の IDE に指示します。 `display_string`としてパラメーターをキャストする[SccMsgDataOnMessage](#LinkSccMsgDataOnMessage)構造体は、ソース管理プラグインによって提供されます。|  
  
## <a name="return-value"></a>戻り値  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_MSG_RTN_OK|文字列の表示または操作が正常に完了します。|  
|SCC_MSG_RTN_CANCEL|ユーザーが操作をキャンセルしようとするとします。|  
  
## <a name="example"></a>例  
 IDE の呼び出しがあると、 [SccGet](../extensibility/sccget-function.md) 20 個のファイル名とします。 ソース管理プラグイン ファイルの取得の途中で操作の取り消しをしないようにしたいです。 各ファイルを取得するには、後`lpTextOutProc`、各ファイルでは、状態情報を渡すと、送信、`SCC_MSG_DOCANCEL`報告する状態が存在しない場合のメッセージします。 かどうか、いつでもプラグイン、戻り値の値を受け取る`SCC_MSG_RTN_CANCEL`IDE から操作をキャンセル、get、すぐにこれ以上ファイルを取得できるようにします。  
  
## <a name="structures"></a>構造体  
  
###  <a name="LinkSccMsgDataIsCancelled"></a> SccMsgDataIsCancelled  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
} SccMsgDataIsCancelled;  
```  
  
 この構造体に送信される、`SCC_MSG_BACKGROUND_IS_CANCELLED`メッセージ。 取り消されたバック グラウンド操作の ID を通信するために使用されます。  
  
###  <a name="LinkSccMsgDataOnBeforeGetFile"></a> SccMsgDataOnBeforeGetFile  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
} SccMsgDataOnBeforeGetFile;  
```  
  
 この構造体に送信される、`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`メッセージ。 取得するファイルの名前と ID の取得を行っているバック グラウンド操作のために使用されます。  
  
###  <a name="LinkSccMsgDataOnAfterGetFile"></a> SccMsgDataOnAfterGetFile  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
   SCCRTN sResult;  
} SccMsgDataOnAfterGetFile;  
```  
  
 この構造体に送信される、`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`メッセージ。 指定したファイルだけを取得するバック グラウンド操作の ID を取得した結果を通信するために使用されます。 戻り値を参照してください、 [SccGet](../extensibility/sccget-function.md)にどのような結果に与えることができます。  
  
###  <a name="LinkSccMsgDataOnMessage"></a> SccMsgDataOnMessage  
 [C++]  
  
```  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szMessage;  
   BOOL bIsError;  
} SccMsgDataOnMessage;  
```  
  
 この構造体に送信される、`SCC_MSG_BACKGROUND_ON_MESSAGE`メッセージ。 バック グラウンド操作の現在の状態を通信するために使用されます。 状態は、IDE に表示する文字列として表されますと`bIsError`、メッセージの重大度を示します (`TRUE`エラー メッセージ。`FALSE`警告または情報メッセージ)。 ステータスを送信するバック グラウンド操作の ID も与えられます。  
  
## <a name="code-example"></a>コード例  
 呼び出し元の簡単な例を次に示します`LPTEXTOUTPROC`を送信する、`SCC_MSG_BACKGROUND_ON_MESSAGE`呼び出しの構造をキャストする方法を示すメッセージ。  
  
```cpp#  
LONG SendStatusMessage(  
    LPTEXTOUTPROC pTextOutProc,  
    DWORD         dwBackgroundID,  
    LPCTSTR       pStatusMsg,  
    BOOL          bIsError)  
{  
    SccMsgDataOnMessage msgData = { 0 };  
    LONG                result  = 0;  
  
    msgData.dwBackgroundOperationID = dwBackgroundID;  
    msgData.szMessage               = pStatusMsg;  
    msgData.bIsError                = bIsError;  
  
    result = pTextOutProc(reinterpret_cast<LPCTSTR>(&msgData), SCC_MSG_BACKGROUND_ON_MESSAGE);  
    return result;  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [IDE によって実装されるコールバック関数](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)

