---
title: ブレークポイントのバインディング |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: efda5969e7022f8c44d7060a29ee31fbc5968d96
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31104152"
---
# <a name="binding-breakpoints"></a>ブレークポイントのバインディング
場合は、ユーザーは、ブレークポイントを設定、おそらく、F9 キーを押して IDE 要求を作成し、デバッグ セッションをブレークポイントを作成するように求められます。  
  
## <a name="setting-a-breakpoint"></a>ブレークポイントの設定  
 ブレークポイントを設定すると、コードまたは、ブレークポイントによって影響を受けるデータがまだ使用できないために 2 段階のプロセスです。 最初に、ブレークポイントを記述する必要があります、次に、コードやデータ使用可能になるようにバインドする必要がそのコードまたはデータに次のように。  
  
1.  ブレークポイントが関連するデバッグ エンジン (DEs) から要求され、し、ブレークポイントとしてバインドされたコードまたはデータの使用可能になります。  
  
2.  ブレークポイントの要求は、すべての関連する DEs に送信する、デバッグ セッションに送信されます。 ブレークポイントを処理することを決めた、DE、対応する保留中のブレークポイントを作成します。  
  
3.  デバッグ セッションは、保留中のブレークポイントを収集し、デバッグ パッケージ (Visual Studio のデバッグのコンポーネント) に返送します。  
  
4.  デバッグ パッケージには、保留中のブレークポイントをコードまたはデータにバインドする、デバッグ セッションが求められます。 デバッグ セッションは、すべての関連する DEs をこの要求を送信します。  
  
5.  デが、ブレークポイントをバインドできる場合は、ブレークポイント、デバッグ セッションに戻るイベントのバインドを送信します。 それ以外の場合は、代わりに、ブレークポイントのエラー イベントを送信します。  
  
## <a name="pending-breakpoints"></a>保留中のブレークポイント  
 保留中のブレークポイントは、コードの複数の場所にバインドできます。 たとえば、C++ テンプレートのソース コードの行は、テンプレートから生成されたすべてのコード シーケンスをバインドできます。 デバッグ セッションは、ブレークポイントにバインドされるイベントを使用して、イベントの送信時に、ブレークポイントにバインドされているコードのコンテキストの列挙します。 コード コンテキストは、DE が複数のブレークポイントがバインド要求ごとにイベントを関連付けられたを送信することがありますので、後でバインドできます。 ただし、デはバインド要求あたり 1 つだけのブレークポイント エラー イベントを送信する必要があります。  
  
## <a name="implementation"></a>実装  
 プログラムでは、デバッグ パッケージ マネージャー (SDM) セッションのデバッグを呼び出して、 [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md)をラップするインターフェイス、 [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md)を記述する構造体、ブレークポイントを設定します。 ブレークポイントでは、さまざまな形式のコードまたはデータ コンテキストに、これらは最終的に解決ができます。  
  
 呼び出して、SDM が関連する各 DE への呼び出しを渡しますその[CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)メソッドです。 これを作成して返しますデ選択した場合、ブレークポイントを処理する、 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)インターフェイスです。 SDM がこれらのインターフェイスを収集し、1 つとしてデバッグ パッケージに渡して`IDebugPendingBreakpoint2`インターフェイスです。  
  
 これまでのイベントは生成されませんでした。  
  
 デバッグ パッケージを呼び出すことによって保留中のブレークポイントをコードまたはデータにバインドする試みます[バインド](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)は、DE によって実装されています。  
  
 ブレークポイントがバインドされている場合、DE を送信、 [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)デバッグ パッケージへのイベント インターフェイスです。 呼び出してブレークポイントまで、コードのすべてのコンテキスト (または 1 つのデータ コンテキスト) を列挙するには、このインターフェイスにバインドされているデバッグ パッケージ使用[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)、1 つまたは複数が返されます[IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)インターフェイスです。 [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)インターフェイスを返します、 [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md)インターフェイス、および[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)を返します、 [BP_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md)コードまたはデータ コンテキストを含む共用体です。  
  
 1 つの送信、DE が、ブレークポイントをバインドできない場合は、 [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)デバッグ パッケージへのイベント インターフェイスです。 デバッグ パッケージがエラーの種類 (エラー/警告) および情報メッセージを呼び出すことによって取得[GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)で始まり、 [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)と[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)です。 これを返します、 [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md)エラーの種類とメッセージを格納する構造体。  
  
 型のエラーを返す場合は、DE、ブレークポイントを処理しますが、バインドできません、`BPET_TYPE_ERROR`です。 デバッグ パッケージが、エラー ダイアログ ボックスを表示することによって応答し、ソース コード行の左側に、ブレークポイント グリフ内の感嘆符グリフが配置されます。  
  
 DE、ブレークポイントの処理しますが、他のバインドできない場合は、DE でバインドが、警告を返します。 IDE は、ソース コード行の左側に、ブレークポイント グリフ内質問グリフを配置することによって応答します。  
  
## <a name="see-also"></a>関連項目  
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)