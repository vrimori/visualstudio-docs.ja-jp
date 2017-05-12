---
title: "アクティブ スクリプトのデバッグの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アクティブ スクリプトのデバッグの概要"
ms.assetid: ce4ec768-d017-4dfa-a7e3-cced3a29e679
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# アクティブ スクリプトのデバッグの概要
アクティブ スクリプトのデバッグ インターフェイスは言語に依存しない、ホスト ニュートラル デバッグを使用すると、さまざまな開発環境をサポートします。  
  
 ![スクリプト ホスト プロセス](../winscript/media/scp56activdbgarchgif.png "Scp56ActivDbgArchgif")  
図 1  
  
 言語に依存しないデバッグ環境がこれらの言語のいずれかの特定の知識がなくても、プログラミング言語のプログラミング言語または組み合わせをサポートできます。  デバッグ環境では、言語な手順やブレークポイントをサポートします。  \(この概要では [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]および VBScript などのスクリプト言語サポートに主に関するものです。\)  
  
 ニュートラル ホスト デバッガーは、Internet Explorer やカスタム ホストのようなすべてのアクティブ スクリプトのホストによって自動的に使用できます。  デバッガーがドキュメント ツリーの構造からデバッグの内容と構文の色指定にユーザーに表示内容とホスト コントロールはついて説明します。  これはデバッグ ソース・コードがホストのドキュメントのコンテキストで示すようになります。  たとえば、Internet Explorer は、HTML ページでスクリプトを示すことができます。  
  
 次の部分では、アクティブなデバッグの主要部分と関連インターフェイスは説明します。  ただし、に進む前に、いくつかは、アクティブなデバッグの概念を定義する必要があります:調整します。  
  
 ホスト アプリケーション  
 スクリプト エンジンをホストする、一連のスクリプト オブジェクト提供するアプリケーション \(または "オブジェクト モデル\)。  
  
 言語エンジン  
 分析を提供するコンポーネント、実行、および特定の言語の抽象化をデバッグします。  
  
 デバッガーの IDE  
 ホスト アプリケーションと言語のエンジンとの通信によってデバッグの UI を提供するアプリケーション。  
  
 コンピューター マネージャーのデバッグ  
 デバッグ可能なアプリケーション プロセスのレジストリを保持するコンポーネント。  
  
 プロセス デバッグ マネージャー  
 特定のアプリケーションのデバッグ可能なドキュメント ツリーを保持するコンポーネントは、実行中のスレッドなどを追跡します。  
  
 ドキュメントのコンテキスト  
 ドキュメントのコンテキストはホスト ドキュメントのソース・コードの特定の範囲を表す抽象化です。  
  
 コンテキストをコード。  
 コード コンテキストを表す言語エンジン \( "仮想の命令ポインター"。\) で実行中のコードの特定の位置を  
  
 式のコンテキスト  
 式が言語エンジンによって評価される可能性がある特定のコンテキスト \(たとえば、スタック フレーム\)。  
  
 オブジェクトの参照  
 "" ウォッチ ウィンドウの UI を実行するために適したオブジェクト名の構造化、言語に依存しない表示、型、値とサブオブジェクト。  
  
 主アクティブなデバッグ コンポーネントと、それらのインターフェイスの詳細に続く関連インターフェイス対応の概要を次に示します。  
  
## 言語のエンジン  
 言語エンジンが提供されます:  
  
-   言語分析および実行する  
  
-   サポート \(ブレークポイントなど\) をデバッグします。  
  
-   式の評価。  
  
-   構文の色。  
  
-   オブジェクトの参照。  
  
-   スタックの列挙体、および分析する。  
  
 デバッグ、式の評価、およびオブジェクトの参照を提供するためにサポートするスクリプト エンジンが必要があるインターフェイスは次のとおりです。  これらのインターフェイスは、デバッガーの UI には文書のコンテキストにエンジンのコード コンテキスト間でマップし、式の評価、スタックの列挙体を参照し、オブジェクトのホスト アプリケーションによって使用されます。  
  
 [IActiveScriptDebug インターフェイス](../winscript/reference/iactivescriptdebug-interface.md)  
 構文の色とコード コンテキストの列挙体を提供します。  
  
 [IActiveScriptErrorDebug インターフェイス](../winscript/reference/iactivescripterrordebug-interface.md)  
 エラーのドキュメントは、スタック フレームのコンテキスト。  
  
 [IActiveScriptSiteDebug インターフェイス](../winscript/reference/iactivescriptsitedebug-interface.md)  
 ホストは、スクリプト エンジンからデバッガーへのリンクを提供します。  
  
 [IDebugCodeContext インターフェイス](../winscript/reference/idebugcodecontext-interface.md)  
 スレッドの仮想 "命令ポインター" です。  
  
 [IEnumDebugCodeContexts インターフェイス](../winscript/reference/ienumdebugcodecontexts-interface.md)  
 ドキュメントのコンテキストに対応するコード コンテキストを列挙します。  
  
 [IDebugStackFrame インターフェイス](../winscript/reference/idebugstackframe-interface.md)  
 スレッドのスタックの論理スタック フレームを表します。  
  
 [IDebugExpressionContext インターフェイス](../winscript/reference/idebugexpressioncontext-interface.md)  
 式を評価することができるコンテキストを提供します。  
  
 [IDebugStackFrameSniffer インターフェイス](../winscript/reference/idebugstackframesniffer-interface.md)  
 論理スタック フレームを列挙する方法を示します。  
  
 [IDebugExpression インターフェイス](../winscript/reference/idebugexpression-interface.md)  
 非同期に評価される式を表します。  
  
 [IDebugSyncOperation インターフェイス](../winscript/reference/idebugsyncoperation-interface.md)  
 スクリプト エンジンがブロックされたスレッドをドットで入れ子中に発生する必要のある操作を抽出できます。  
  
 [IDebugAsyncOperation インターフェイス](../winscript/reference/idebugasyncoperation-interface.md)  
 同期デバッグの非同期操作へのアクセスを提供します。  
  
 [IDebugAsyncOperationCallBack インターフェイス](../winscript/reference/idebugasyncoperationcallback-interface.md)  
 `IDebugAsyncOperation` のインターフェイスの評価の進行状況に関する状態のイベントを提供します。  
  
 [IEnumDebugExpressionContexts インターフェイス](../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
 `IDebugExpressionContexts` のオブジェクトのコレクションを列挙します。  
  
 [IProvideExpressionContexts インターフェイス](../winscript/reference/iprovideexpressioncontexts-interface.md)  
 特定のコンポーネントによって認識される式のコンテキストを列挙する方法を示します。  
  
 [IDebugFormatter インターフェイス](../winscript/reference/idebugformatter-interface.md)  
 言語が IDE または変数の値の間の変換や VARTYPE 型と文字列カスタマイズできます。  
  
 [IDebugStackFrameSnifferEx インターフェイス](../winscript/reference/idebugstackframesnifferex-interface.md)  
 PDM の論理スタック フレームを列挙します。  
  
## ホスト  
 :ホスト  
  
-   言語エンジンをホストします。  
  
-   オブジェクト モデル \(スクリプトがあります\) オブジェクトのセットを提供します。  
  
-   デバッグできるとコンテンツ ドキュメント ツリーを定義します。  
  
-   仮想アプリケーションにスクリプトを整理します。  
  
 2 種類のホストがあります:  
  
-   物の言えないホストは、基本的な Active スクリプトのインターフェイスをサポートします。  これは、文書の構造や編成を制御できません; これは、言語エンジンに提供されるスクリプトによって完全に決定されます。  
  
-   ホストは、スマート ドキュメント ツリー、ドキュメントの内容と構文の色指定を定義するために、より多くのインターフェイスをサポートします。  次の部分で説明する一連のホストがスマート ホストになるようにそれをより簡単にするヘルパー インターフェイスを持ちます。  
  
### スマート ホストのヘルパー インターフェイス  
 `IDebugDocumentHelper` のメソッドは完全なホストのインターフェイスの完全な複雑さ \(および累乗\) を処理しないでスマート ホストを向上させるためにホストが使用できる単純一連のインターフェイスを提供します。  
  
 ホストは、これらのインターフェイスを使用する必要はありません。  ただし、これらのインターフェイスを使用して一部のより複雑なインターフェイスを実装するか、またはを使用することを回避できます。  
  
 [IDebugDocumentHelper インターフェイス](../winscript/reference/idebugdocumenthelper-interface.md)  
 PDM によって実装されたスマート ホストに必要な追加のインターフェイスを実装します。  
  
 [IDebugDocumentHost インターフェイス](../winscript/reference/idebugdocumenthost-interface.md)  
 デバッガーに対して、ホスト固有の機能を、構文配色など、公開する \(省略可能\) ホストによって実装されます。  
  
 詳細については、「[スマート ホスト ヘルパー インターフェイスの実装](../winscript/implementing-smart-host-helper-interfaces.md)」を参照してください。  
  
### 完全なスマートのホスト インターフェイス  
 ヘルパー インターフェイスを使用するスマート使用するホストが実装するか、あるインターフェイスの完全なセットを次に示します。  
  
 ホストによって実装されたインターフェイス:  
  
 [IDebugDocumentInfo インターフェイス](../winscript/reference/idebugdocumentinfo-interface.md)  
 いる可能性がある、またははインスタンス化されないドキュメントについて説明します。  
  
 [IDebugDocumentProvider インターフェイス](../winscript/reference/idebugdocumentprovider-interface.md)  
 ドキュメントをオンデマンドでインスタンス化する手段です。  
  
 [IDebugDocument インターフェイス](../winscript/reference/idebugdocument-interface.md)  
 すべてのデバッグ ドキュメントの基本インターフェイス。  
  
 [IDebugDocumentText インターフェイス](../winscript/reference/idebugdocumenttext-interface.md)  
 デバッグのドキュメントのテキストのみのバージョンへのアクセスを提供します。  
  
 [IDebugDocumentTextAuthor インターフェイス](../winscript/reference/idebugdocumenttextauthor-interface.md)  
 デバッグのドキュメントのテキストのみのバージョンの編集を許可します。  
  
 [IDebugDocumentContext インターフェイス](../winscript/reference/idebugdocumentcontext-interface.md)  
 デバッグ ドキュメントの部分の抽象的に表示されます。  
  
 ホストに代わって PDM によって実装されるインターフェイス:  
  
 [IDebugApplicationNode インターフェイス](../winscript/reference/idebugapplicationnode-interface.md)  
 プロジェクト ツリー内のコンテキストを提供することで `IDebugDocumentProvider` のインターフェイスの機能を拡張します。  
  
## デバッガーの IDE  
 IDE では、言語に依存しないデバッグの UI です。  これは提供されます:  
  
-   ドキュメント ビューアー\/エディター。  
  
-   ブレークポイント管理。  
  
-   式の評価、ウォッチ ウィンドウ。  
  
-   スタック フレームの参照。  
  
-   オブジェクトとクラスの参照。  
  
-   仮想アプリケーション構造の参照。  
  
 デバッガーが実装するインターフェイス:  
  
 [IApplicationDebugger インターフェイス](../winscript/reference/iapplicationdebugger-interface.md)  
 デバッガーの IDE セッションを公開する主要なインターフェイス。  
  
 [IApplicationDebuggerUI インターフェイス](../winscript/reference/iapplicationdebuggerui-interface.md)  
 外部コンポーネントにデバッガーのユーザー インターフェイス \(UI\) をより細かく制御できます。  
  
 [IDebugExpressionCallBack インターフェイス](../winscript/reference/idebugexpressioncallback-interface.md)  
 `IDebugExpression` の評価の進行状況の状態に対するイベントを提供します。  
  
 [IDebugDocumentTextEvents インターフェイス](../winscript/reference/idebugdocumenttextevents-interface.md)  
 関連付けられたテキスト ドキュメントへの変更を示すイベントを提供します。  
  
 [IDebugApplicationNodeEvents インターフェイス](../winscript/reference/idebugapplicationnodeevents-interface.md)  
 `IDebugApplicationNode` のインターフェイスにイベント インターフェイスを提供します。  
  
### コンピューター マネージャーのデバッグ  
 コンピューターのデバッグ マネージャーは、アクティブな仮想アプリケーションのリストを保持し、列挙することにより、仮想アプリケーションとデバッガーの間に接続ポイントを提供します。  
  
 [IDebugSessionProvider インターフェイス](../winscript/reference/idebugsessionprovider-interface.md)  
 実行中のアプリケーションのデバッグ セッションを設定します。  
  
 [IMachineDebugManager インターフェイス](../winscript/reference/imachinedebugmanager-interface.md)  
 コンピューターのデバッグ マネージャーへの主要なインターフェイス。  
  
 [IMachineDebugManagerCookie インターフェイス](../winscript/reference/imachinedebugmanagercookie-interface.md)  
 `IMachineDebugManager` のインターフェイスが、このインターフェイスに似たデバッグのクッキーをサポートします。  
  
 [IMachineDebugManagerEvents インターフェイス](../winscript/reference/imachinedebugmanagerevents-interface.md)  
 コンピューターで保持される実行中のアプリケーションのリストの変更通知のは、マネージャーをデバッグします。  
  
 [IEnumRemoteDebugApplications インターフェイス](../winscript/reference/ienumremotedebugapplications-interface.md)  
 を実行しているコンピューターにアプリケーションを列挙します。  
  
### プロセス デバッグ マネージャー  
 : PDM は次の処理を行います。  
  
-   複数言語のデバッグ エンジンを同期します。  
  
-   デバッグ可能なドキュメント ツリーを保持します。  
  
-   スタック フレームをマージします。  
  
-   言語エンジンで座標のブレークポイントと手順。  
  
-   トラックのスレッド。  
  
-   非同期処理のデバッガーのスレッドが保持されます。  
  
-   コンピューターのデバッグ マネージャーおよびデバッガーの IDE と通信します。  
  
 以下は、プロセス デバッグ マネージャーが提供するインターフェイスです。  
  
 [IProcessDebugManager インターフェイス](../winscript/reference/iprocessdebugmanager-interface.md)  
 プロセス デバッグ マネージャーへの主要なインターフェイス。  このインターフェイスは、プロセスから仮想アプリケーションを作成するか、追加、または削除できます。  
  
 [IRemoteDebugApplication インターフェイス](../winscript/reference/iremotedebugapplication-interface.md)  
 実行中のアプリケーションを表します。  
  
 [IDebugApplication インターフェイス](../winscript/reference/idebugapplication-interface.md)  
 言語のエンジンとホストによって使用されるのはリモート デバッグのメソッドを公開します。  
  
 [IRemoteDebugApplicationThread インターフェイス](../winscript/reference/iremotedebugapplicationthread-interface.md)  
 特定のアプリケーション内の実行中のスレッドを表します。  
  
 [IDebugApplicationThread インターフェイス](../winscript/reference/idebugapplicationthread-interface.md)  
 言語のエンジンとホストがスレッドの同期を提供し、スレッド固有のデバッグ状態情報を管理します。  
  
 [IEnumRemoteDebugApplicationThreads インターフェイス](../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
 アプリケーションの実行中のスレッドを列挙します。  
  
 [IDebugThreadCall インターフェイス](../winscript/reference/idebugthreadcall-interface.md)  
 ディスパッチでマーシャリングされた呼び出し。  
  
 [IDebugApplicationNode インターフェイス](../winscript/reference/idebugapplicationnode-interface.md)  
 階層のドキュメントの位置を維持します。  
  
 [IEnumDebugApplicationNodes インターフェイス](../winscript/reference/ienumdebugapplicationnodes-interface.md)  
 アプリケーションに関連付けられているノードの子ノードを列挙します。  
  
 [IEnumDebugStackFrames インターフェイス](../winscript/reference/ienumdebugstackframes-interface.md)  
 エンジンからマージされたスレッドに対応するスタック フレームを列挙します。  
  
 [IDebugCookie インターフェイス](../winscript/reference/idebugcookie-interface.md)  
 デバッグのクッキーがスクリプト デバッガーで設定できます。  
  
 [IDebugHelper インターフェイス](../winscript/reference/idebughelper-interface.md)  
 スクリプト エンジンのオブジェクト ブラウザーと単純なコネクション ポイントのファクトリとして機能します。  
  
 [ISimpleConnectionPoint インターフェイス](../winscript/reference/isimpleconnectionpoint-interface.md)  
 スクリプト エンジンの特定のコネクション ポイントで発生したイベントについて説明し、列挙する単純な方法を提供します。  
  
## 参照  
 [アクティブ スクリプト デバッガー インターフェイス](../winscript/reference/active-script-debugger-interfaces.md)