---
title: "LPTEXTOUTPROC |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
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
caps.latest.revision: 21
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
ms.openlocfilehash: 7229d2681912663ad2cddcf95e140197495c0934
ms.lasthandoff: 02/22/2017

---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC
ユーザーは、統合開発環境 (IDE) 内からソース管理操作を実行するとき、ソース管理プラグインすることも、操作に関連するエラー状態や状態のメッセージの伝達します。 プラグインを表示できます独自のメッセージ ボックスこの目的のため。 ただし、シームレスな統合の詳細では、プラグイン文字列渡すことが状態情報を表示するがネイティブの方法でそれらを表示すると、IDE にします。 このメカニズムは、`LPTEXTOUTPROC`関数ポインター。 IDE では、エラーと状態を表示するため (詳細については、以下で説明) この関数を実装します。  
  
 IDE をソース管理プラグインをこの関数に関数ポインターとして渡す、`lpTextOutProc`呼び出すときに、パラメーター、 [SccOpenProject](../extensibility/sccopenproject-function.md)します。 呼び出しの途中での例については、SCC 操作中に、 [SccGet](../extensibility/sccget-function.md)多数のファイルを含む、プラグイン、呼び出すことができます、`LPTEXTOUTPROC`定期的に表示する文字列を渡す関数です。 IDE は、または必要に応じての個別のメッセージ ボックスに、出力ウィンドウには、ステータス バーにこれらの文字列を表示することがあります。 必要に応じて、IDE がで特定のメッセージを表示することがあります、**キャンセル** ボタンをクリックします。 これにより、ユーザーは、操作をキャンセルし、IDE をプラグインにこの情報を渡す機能を提供します。  
  
## <a name="signature"></a>署名  
 IDE の関数は、次のシグネチャを持つ出力します。  
  
```cpp#  
typedef LONG (*LPTEXTOUTPROC) (  
   LPSTR display_string,  
   LONG mesg_type  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 display_string  
 表示するテキスト文字列。 この文字列は、キャリッジ リターン、ライン フィードで終了しない必要があります。  
  
 mesg_type  
 メッセージの種類。 次の表では、このパラメーターにサポートされている値を示します。  
  
|値|説明|  
|-----------|-----------------|  
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|メッセージは、情報、警告、またはエラーと見なされます。|  
|`SCC_MSG_STATUS`|メッセージは、状態が表示され、ステータス バーに表示されることができます。|  
|`SCC_MSG_DOCANCEL`|送信メッセージ文字列がありません。|  
|`SCC_MSG_STARTCANCEL`|表示の開始、**キャンセル** ボタンをクリックします。|  
|`SCC_MSG_STOPCANCEL`|表示を停止する、**キャンセル** ボタンをクリックします。|  
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|IDE を要求するかどうかはバック グラウンド操作をキャンセルできるが: IDE 返します`SCC_MSG_RTN_CANCEL`操作がキャンセルされた場合、それ以外の場合を返します`SCC_MSG_RTN_OK`します。 `display_string`パラメーターとしてキャスト、 [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled)構造体は、ソース管理プラグインによって提供されます。|  
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|バージョン コントロールから取得されるまで、ファイルは、IDE に指示します。 `display_string`パラメーターとしてキャスト、 [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile)構造体は、ソース管理プラグインによって提供されます。|  
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|バージョン コントロールから取得された後、ファイルは、IDE に指示します。 `display_string`パラメーターとしてキャスト、 [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile)構造体は、ソース管理プラグインによって提供されます。|  
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|バック グラウンド操作の現在の状態の IDE に指示します。 `display_string`パラメーターとしてキャスト、 [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage)構造体は、ソース管理プラグインによって提供されます。|  
  
## <a name="return-value"></a>戻り値  
  
|値|説明|  
|-----------|-----------------|  
|SCC_MSG_RTN_OK|文字列の表示または操作が正常に完了します。|  
|SCC_MSG_RTN_CANCEL|ユーザーが操作をキャンセルしようとするとします。|  
  
## <a name="example"></a>例  
 たとえば、IDE の呼び出し、 [SccGet](../extensibility/sccget-function.md)&20; 個のファイル名を持つ。 ソース管理プラグイン ファイルの取得の途中で操作を取り消すようにしたいです。 各ファイルを取得した後を呼び出します`lpTextOutProc`、ファイルごとにステータス情報を渡すと、送信、`SCC_MSG_DOCANCEL`メッセージの報告する状態が存在しない場合。 かどうかはいつでもを受け取るの戻り値`SCC_MSG_RTN_CANCEL`IDE から操作をキャンセル、get、すぐをこれ以上ファイルを取得するためです。  
  
## <a name="structures"></a>構造体  
  
###  <a name="a-namelinksccmsgdataiscancelleda-sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a>SccMsgDataIsCancelled  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
} SccMsgDataIsCancelled;  
```  
  
 と共にこの構造体が送信される、`SCC_MSG_BACKGROUND_IS_CANCELLED`メッセージです。 取り消された、バック グラウンド操作の ID を通信するために使用されます。  
  
###  <a name="a-namelinksccmsgdataonbeforegetfilea-sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a>SccMsgDataOnBeforeGetFile  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
} SccMsgDataOnBeforeGetFile;  
```  
  
 と共にこの構造体が送信される、`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`メッセージです。 取得するファイルの名前と、取得を行っているバック グラウンド操作の ID を通信するために使用されます。  
  
###  <a name="a-namelinksccmsgdataonaftergetfilea-sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a>SccMsgDataOnAfterGetFile  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
   SCCRTN sResult;  
} SccMsgDataOnAfterGetFile;  
```  
  
 と共にこの構造体が送信される、`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`メッセージです。 指定されたファイルだけでなく、取得するには、バック グラウンド操作の ID を取得する結果を通信するために使用されます。 戻り値を参照してください、 [SccGet](../extensibility/sccget-function.md)にどのような結果に与えることができます。  
  
###  <a name="a-namelinksccmsgdataonmessagea-sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a>SccMsgDataOnMessage  
 [C++]  
  
```  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szMessage;  
   BOOL bIsError;  
} SccMsgDataOnMessage;  
```  
  
 と共にこの構造体が送信される、`SCC_MSG_BACKGROUND_ON_MESSAGE`メッセージです。 バック グラウンド操作の現在の状態を通信するために使用されます。 状態は、IDE で表示される文字列で表したと`bIsError`メッセージの重大度を示します (`TRUE`にエラー メッセージです。`FALSE`警告や情報メッセージ)。 ステータスを送信するバック グラウンド操作の ID も示されます。  
  
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
 [IDE で実装されるコールバック関数](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)
