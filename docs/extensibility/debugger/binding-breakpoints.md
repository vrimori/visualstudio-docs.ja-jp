---
title: ブレークポイントのバインディング |Microsoft Docs
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
ms.openlocfilehash: e02b3da843f7e4cffe33d660a8a82ab3c4c0dc03
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153447"
---
# <a name="bind-breakpoints"></a>ブレークポイントをバインドします。
キーを押してにかどうか、ユーザーが、ブレークポイントをおそらく設定**F9**IDE が要求を作成し、ブレークポイントを作成する、デバッグ セッションを求めます。  
  
## <a name="set-a-breakpoint"></a>ブレークポイントの設定  
 コードまたはブレークポイントによって影響を受けるデータがまだ利用できないために、2 段階のプロセスは、ブレークポイントを設定します。 最初に、ブレークポイントを記述する必要がある、次に、コードまたはデータが使用可能なにする必要がありますにバインドするコードやデータ、する次のように。  
  
1.  ブレークポイントが関連するデバッグ エンジン (DEs) から要求され、ブレークポイントがコードまたはデータにバインドされている利用可能になったします。  
  
2.  ブレークポイント要求は、すべての関連する DEs に送信する、デバッグ セッションに送信されます。 ブレークポイントを処理することを選択した任意の DE、対応する保留中のブレークポイントを作成します。  
  
3.  デバッグ セッションは、保留中のブレークポイントを収集し、パッケージのデバッグ (Visual Studio のデバッグのコンポーネント) に返送します。  
  
4.  パッケージのデバッグには、保留中のブレークポイントをコードまたはデータにバインドする、デバッグ セッションが求められます。 デバッグ セッションでは、すべての関連する DEs をこの要求を送信します。  
  
5.  デが、ブレークポイントをバインドできない場合は、ブレークポイント、デバッグ セッションにイベントのバインドを送信します。 それ以外の場合は、ブレークポイントのエラー イベントを代わりに送信します。  
  
## <a name="pending-breakpoints"></a>保留中のブレークポイント  
 保留中のブレークポイントは、複数のコードの場所にバインドできます。 たとえば、C++ テンプレートのソース コードの行は、テンプレートから生成されたすべてのコード シーケンスにバインドできます。 デバッグ セッションは、イベントの送信時に、ブレークポイントにバインドされているコードのコンテキストを列挙するために、ブレークポイントにバインドされるイベントを使用できます。 コード コンテキストの詳細については、DE が複数のブレークポイントにバインドされたイベントの各バインド要求を送信するため、後でバインドできます。 ただし、DE は、バインド要求ごとに 1 つだけのブレークポイント エラー イベントを送信する必要があります。  
  
## <a name="implementation"></a>実装  
 プログラムでは、パッケージのデバッグのセッション デバッグ マネージャー (SDM) の呼び出しを付けます、 [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md)インターフェイスをラップする、 [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md)構造について説明しますが、ブレークポイントを設定します。 ブレークポイントでは、さまざまな形式のコードまたはデータ コンテキストに、最終的に解決ができます。  
  
 呼び出して、SDM がこの呼び出しに関連する各 DE を渡しますその[CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)メソッド。 作成して、返しますが、DE 選択した場合、ブレークポイントを処理するために、 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)インターフェイス。 SDM は、これらのインターフェイスを収集し、1 つとして、デバッグ パッケージに渡さ`IDebugPendingBreakpoint2`インターフェイス。  
  
 これまでに生成されているイベントはありません。  
  
 デバッグ パッケージを呼び出すことによって保留中のブレークポイントをコードまたはデータにバインドする試みます[バインド](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)、デによって実装されます。  
  
 ブレークポイントがバインドされている場合、DE の送信、 [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)デバッグ パッケージにイベントのインターフェイス。 呼び出すことで、ブレークポイントをすべてのコード コンテキスト (または 1 つのデータ コンテキスト) を列挙するには、このインターフェイスにバインドされているデバッグ パッケージは[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)、1 つまたは複数を返す[IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)インターフェイス。 [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)インターフェイスを返します、 [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md)インターフェイス、および[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)を返します、 [BP_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md)コードまたはデータ コンテキストを含む共用体。  
  
 1 つの送信、DE が、ブレークポイントをバインドできない場合は、 [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)デバッグ パッケージにイベントのインターフェイス。 デバッグ パッケージは、呼び出すことによって、エラーの種類 (エラーまたは警告) と情報メッセージを取得します[GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)、その後に[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)と[。GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)します。 これにより返されます、 [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md)エラーの種類とメッセージを含む構造体。  
  
 型のエラーを返します、DE でブレークポイントを処理している場合、バインドできません、`BPET_TYPE_ERROR`します。 デバッグ パッケージが、エラー ダイアログ ボックスを表示することで応答し、ソース コード行の左側に、ブレークポイント グリフ内の感嘆符グリフが配置されます。  
  
 DE、ブレークポイントの処理、他が、バインドできない場合は、DE でバインドが、警告を返します。 IDE は、ソース コード行の左側に、ブレークポイント グリフを内部で質問のグリフを配置することで応答します。  
  
## <a name="see-also"></a>関連項目  
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)