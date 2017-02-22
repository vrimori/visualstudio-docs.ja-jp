---
title: "ブレークポイントのバインディング | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ブレークポイントのバインディング"
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# ブレークポイントのバインディング
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

要求IDE を生成しデバッグ セッションのブレークポイントを作成するように要求しますがユーザーが F9 キーを押すとブレークポイントを示します。  
  
## ブレークポイントの設定  
 ブレークポイントを設定するとブレークポイントの影響を受けるコードまたはデータが利用できない可能性があるため行の手順です。  次のように最初にコードまたはデータが使用可能になるとブレークポイントで説明する次にそのコードまたはデータにバインドする必要があります :  
  
1.  ブレークポイントは関連するデバッグ エンジン \(DEs\) から要求され使用可能になるとブレークポイントはコードまたはデータにバインドします。  
  
2.  ブレークポイントの要求はすべての関連 DEs に送信するデバッグ セッションに渡されます。  ブレークポイントを処理するために選択した DE が保留中のブレークポイントの対応を作成します。  
  
3.  デバッグ セッションで保留中のブレークポイントを収集しデバッグのパッケージ \(Visual Studio のデバッグ コンポーネント\) を返します。  
  
4.  デバッグのパッケージによってデバッグ セッションがコードまたはデータに保留中のブレークポイントをバインドするように求められます。  デバッグ セッションに関連するすべての DEsこの要求を送信します。  
  
5.  ブレークポイントをバインドしますがデバッグ セッションにブレークポイントにバインドされたイベントを返します。  でない場合はブレークポイントのエラー イベントを送信します。  
  
## 保留中のブレークポイント  
 保留中のブレークポイントのコード位置にバインドできます。  たとえばC.C\+\+ テンプレートのソース・コードの行はテンプレート コードから生成されたシーケンスにバインドできます。  デバッグ セッションのイベントが送信とブレークポイントにバインドされているコード コンテキストを列挙するにはブレークポイントのバインド イベントを使用できます。  詳細については後でコード コンテキスト バインドすることでde\-DE は複数のブレークポイントにバインドされた各要求に対してバインドのイベントを送信する場合があります。  ただしde\-DE はバインド要求ごとに 1 回のブレークポイントのエラー イベントのみを送信する必要があります。  
  
## 実装  
 プログラムでパッケージはデバッグ セッションのデバッグ マネージャーを呼び出し\(SDM\) を設定するブレークポイントを記述する [BP\_REQUEST\_INFO](../../extensibility/debugger/reference/bp-request-info.md) の構造をラップする [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) のインターフェイスを提供します。  ブレークポイントはさまざまなフォームですがコードまたはデータ コンテキストに最終的に解決されます。  
  
 SDM は関連する de\-DE に [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) のメソッドを呼び出しこの呼び出しを渡します。  ブレークポイントを処理する DE を選択した場合 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) のインターフェイスを作成して返します。  SDM はこれらのインターフェイスを収集しデバッグのパッケージへの `IDebugPendingBreakpoint2` の一つのインターフェイスとして渡します。  
  
 この時点ではイベントは生成されません。  
  
 デバッグのパッケージは[バインド](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) の de\-DE によって実装される呼び出してコードまたはデータに保留中のブレークポイントをバインドしようとします。  
  
 ブレークポイントをバインドするとde\-DE sends デバッグ パッケージに [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) のイベント インターフェイス。  デバッグのパッケージは [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) の [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) の一つ以上のインターフェイスを返す呼び出してブレークポイントにバインドされたすべてのコード コンテキスト \(つまり一つのデータ コンテキスト\) を列挙するにはこのインターフェイスを使用します。  [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) の [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) インターフェイスはインターフェイスおよび [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) を返します。コードまたはデータ コンテキストを含む共用体の [BP\_RESOLUTION\_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) 返します。  
  
 DE はブレークポイントをバインドするデバッグのあるパッケージに一つの [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) のイベント インターフェイスを送信します。  デバッグのパッケージは [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) と [GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) に続く [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) を呼び出してエラーの種類 \(エラーまたは警告\) と情報メッセージを取得します。  これはエラーの種類とメッセージを含む [BP\_ERROR\_RESOLUTION\_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) の構造体を返します。  
  
 DE handles がブレークポイントのバインド型 `BPET_TYPE_ERROR` のエラーを返します。  デバッグのパッケージはエラー\] ダイアログ ボックスを表示しソース・コードの行の左側にIDE の場所でブレークポイントのグリフ内の感嘆符のグリフ応答します。  
  
 DE handles がブレークポイントのバインドできませんが他の de\-DE にコントロールをバインドする場合警告を返します。  IDE はソース・コード行の左側にブレークポイントのグリフ内の質問グリフを追加することにより応答します。  
  
## 参照  
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)