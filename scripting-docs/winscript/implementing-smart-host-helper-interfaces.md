---
title: "スマート ホスト ヘルパー インターフェイスの実装 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "スマート ホスト ヘルパー インターフェイス, 実装"
ms.assetid: b9c44246-4d4d-469e-91be-00c8f5796fa5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# スマート ホスト ヘルパー インターフェイスの実装
[IDebugDocumentHelper インターフェイス](../winscript/reference/idebugdocumenthelper-interface.md) のインターフェイスは、スマート ホストに必要な追加のインターフェイスを実装するため、アクティブなデバッグ用のスマート ホストを作成するタスクが大幅に簡略化されます。  
  
 `IDebugDocumentHelper`を使用してスマート ホストであるため、ホスト アプリケーションは、次の 3 点のみする必要があります:  
  
1.  `CoCreate` は、プロセス デバッグ マネージャー、デバッグ可能アプリケーションの一覧にアプリケーションを追加するに [IProcessDebugManager インターフェイス](../winscript/reference/iprocessdebugmanager-interface.md) のインターフェイスを使用します。  
  
2.  [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md) のメソッドを使用して各スクリプト オブジェクトのデバッグに関するドキュメントのヘルパーを作成します。  ドキュメント名、親ドキュメント、テキスト、およびスクリプト ブロックが定義されていることを確認します。  
  
3.  では、オブジェクトの [IActiveScriptSiteDebug インターフェイス](../winscript/reference/iactivescriptsitedebug-interface.md) のインターフェイスを実装する \(Active スクリプトが必要に応じて\) [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) のインターフェイス実装します。  ヘルパーへの `IActiveScriptSiteDebug` のインターフェイスだけにデリゲートの唯一の重要なメソッド。  
  
 必要に応じて、ホストは構文の色、ドキュメントのコンテキストの作成および他の拡張機能のコントロールが必要な場合は [IDebugDocumentHost インターフェイス](../winscript/reference/idebugdocumenthost-interface.md) のインターフェイスを実装できます。  
  
 スマート ホストのヘルパーの主要な制限は \(ドキュメントを配置できますが\) 追加した後にのみコンテンツが縮小または変更するドキュメントを扱うことができます。  ただし、ほとんどのスマート ホストに対して、が提供する機能は、必要な要素です。  
  
 次のセクションでは、各手順を詳しく説明します。  
  
## アプリケーション オブジェクトを作成します。  
 スマート ホストのヘルパーを使用できるようにデバッガーでアプリケーションを表すために [IDebugApplication インターフェイス](../winscript/reference/idebugapplication-interface.md) のオブジェクトを作成する必要があります。  
  
#### アプリケーション オブジェクトを作成するには  
  
1.  `CoCreateInstance`を使用しているプロセス デバッグ マネージャーのインスタンスを作成します。  
  
2.  [IProcessDebugManager::CreateApplication](../winscript/reference/iprocessdebugmanager-createapplication.md) を呼び出します。  
  
3.  [IDebugApplication::SetName](../winscript/reference/idebugapplication-setname.md)を使用してアプリケーションの名前を設定します。  
  
4.  [IProcessDebugManager::AddApplication](../winscript/reference/iprocessdebugmanager-addapplication.md)を使用してデバッグ可能なアプリケーションのリストへのアプリケーション オブジェクトを追加します。  
  
     アウトラインの下のコードは、プロセスただし、エラー チェックやそのほかの信頼性の高いプログラミング手法は含まれません。  
  
    ```  
    CoCreateInstance(CLSID_ProcessDebugManager, NULL,  
          CLSCTX_INPROC_SERVER | CLSCTX_INPROC_HANDLER  
          | CLSCTX_LOCAL_SERVER,  
    IID_IProcessDebugManager, (void **)&g_ppdm);  
    g_ppdm->CreateApplication(&g_pda);  
    g_pda->SetName(L"My cool application");  
    g_ppdm->AddApplication(g_pda, &g_dwAppCookie);  
    ```  
  
## を使用して IDebugDocumentHelper  
  
#### 使用するヘルパー \(最小限の手順のシーケンス\) を  
  
1.  各ホストのドキュメントで、[IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)を使用するヘルパーを作成します。  
  
2.  名前は、ドキュメントの属性設定、ヘルパー [IDebugDocumentHelper::Init](../winscript/reference/idebugdocumenthelper-init.md) などを呼び出します。  
  
3.  ドキュメントがルート ツリーのドキュメントの位置を定義し、デバッガーから参照できるようにするために、ドキュメントの親のヘルパーとの [IDebugDocumentHelper::Attach](../winscript/reference/idebugdocumenthelper-attach.md) \(または無効にします。\) を呼び出します。  
  
4.  ドキュメントのテキストを定義するに [IDebugDocumentHelper::AddDBCSText](../winscript/reference/idebugdocumenthelper-adddbcstext.md) か [IDebugDocumentHelper::AddUnicodeText](../winscript/reference/idebugdocumenthelper-addunicodetext.md) を呼び出します。   \(これらはドキュメントがインクリメンタル ダウンロードするときに複数回呼び出すことができますが、ブラウザーのように\)。  
  
5.  各スクリプト ブロックと関連付けられたスクリプト エンジンの範囲を定義します [IDebugDocumentHelper::DefineScriptBlock](../winscript/reference/idebugdocumenthelper-definescriptblock.md)。  
  
## IActiveScriptSiteDebug の実行  
 次のように、[IActiveScriptSiteDebug::GetDocumentContextFromPosition](../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)を実装するには、ヘルパーを特定のサイトに対応する取得し、開始のドキュメントを特定のソースのコンテキストにオフセットを取得します:  
  
```  
pddh->GetScriptBlockInfo(dwSourceContext, NULL, &ulStartPos, NULL);  
```  
  
 次に、指定されたオフセット文字の新しい文書のコンテキストを作成するには、ヘルパーの使用:  
  
```  
pddh->CreateDebugDocumentContext(ulStartPos + uCharacterOffset, cChars, &pddcNew);  
```  
  
 [IActiveScriptSiteDebug::GetRootApplicationNode](../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)を実装するには、`IDebugApplication::GetRootNode` を呼び出すだけです。[IRemoteDebugApplication::GetRootNode](../winscript/reference/iremotedebugapplication-getrootnode.md) \(から継承\)  
  
 [IDebugDocumentHelper::GetDebugApplicationNode](../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md)を実行するには、プロセス デバッグ マネージャーを使用して作成した `IDebugApplication` を返します。  
  
## IDebugDocumentHost の省略可能なインターフェイス  
 ホストは、ヘルパーのコントロールを付けるために [IDebugDocumentHelper::SetDebugDocumentHost](../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md) を使用して [IDebugDocumentHost インターフェイス](../winscript/reference/idebugdocumenthost-interface.md) の実装を提供できます。  ホストのインターフェイスができる主な三つの一部を次に示します。:  
  
-   ホストが、実際の文字をすばやく指定する必要がないように [IDebugDocumentHelper::AddDeferredText](../winscript/reference/idebugdocumenthelper-adddeferredtext.md) を使用してテキストを追加します。  文字が実際に必要である場合、ホストのヘルパー関数は [IDebugDocumentHost::GetDeferredText](../winscript/reference/idebugdocumenthost-getdeferredtext.md)。  
  
-   ヘルパーによって提供される既定の構文の色指定をオーバーライドします。  ヘルパーは既定の実装にある文字の範囲の色指定を確認するに [IDebugDocumentHost::GetScriptTextAttributes](../winscript/reference/idebugdocumenthost-getscripttextattributes.md) をホストに返します `E_NOTIMPL`呼び出します。  
  
-   [IDebugDocumentHost::OnCreateDocumentContext](../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)を実行してヘルパーが作成するドキュメントのコンテキストにコントロールのワイルドカードを提供します。  これにより、ホストは既定のドキュメントのコンテキストの実装の機能をオーバーライドできます。  
  
-   ドキュメントに、ファイル システムのパス名を指定します。  ドキュメントへの変更を編集、保存する UI のデバッグ使用方法。  [IDebugDocumentHost::NotifyChanged](../winscript/reference/idebugdocumenthost-notifychanged.md) は、文書が保存されるとをホストに通知するために呼び出されます。  
  
## 参照  
 [アクティブ スクリプトのデバッグの概要](../winscript/active-script-debugging-overview.md)