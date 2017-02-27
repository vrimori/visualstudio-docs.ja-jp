---
title: "IntelliSense をホストしています。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] レガシーの IntelliSense をホストしています。"
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# IntelliSense をホストしています。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio ではIntelliSense のホストを可能にします。  IntellSense のホストはVisual Studio テキスト エディターでホスティングコード用の IntelliSense を提供することができます。  
  
## ホスト IntelliSense を使用  
 Visual Studio でのコードは入力候補セットへのアクセスとテキスト バッファーはユーザー インターフェイスからの IntelliSense ウィンドウの任意の場所にを取得できます \(UI\)。  次の例のシナリオは\[ENT0ENT\] ウィンドウでブレークポイントのプロパティ ウィンドウの条件のフィールドを完了します。  
  
### インターフェイスの実装  
  
#### IVsIntellisenseHost  
 IntelliSense のポップアップ ウィンドウをホストする UI コンポーネントが <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> インターフェイスをサポートする必要があります。  既定のコア エディターのテキスト ビューではIntelliSense の現在の機能を保持するに <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> の標準的なインターフェイスの実装が含まれています。  ほとんどの場合<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> のインターフェイスのメソッドは実行される項目の <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> インターフェイスのサブセットを表します。  IntelliSense のサブセットはキャレット UI 処理と選択操作や単純なテキストの置換の機能が含まれます。  また<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> のインターフェイスでは IntelliSense がコンテキストに使用されるテキスト バッファーにない件名に提供できるようにIntelliSense を 「あります」。context 」内。  
  
#### IVsIntellisenseHost.GetHostFlags  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> インターフェイスのプロバイダーはどのような IntelliSense のサポートがホストを使用するかを判断します。クライアントができるように <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> のメソッドを実装する必要があります。  
  
 [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md) で定義されているホストでフラグは次に示します。  
  
|IntelliSense のホストのフラグ|Description|  
|---------------------------|-----------------|  
|IHF\_READONLYCONTEXT|このフラグを設定するとコンテキスト バッファーが読み取り専用であり編集がサブジェクト テキスト内でのみ発生することを意味します。|  
|IHF\_NOSEPERATESUBJECT|このフラグを設定するとIntelliSense の別の項目がないことを示します。  キーワードは <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 従来の IntelliSense システムなどのコンテキスト バッファーになります。|  
|IHF\_SINGLELINESUBJECT|このフラグを設定するとサブジェクトが複数行できないことを意味します ENT0ENT \[出力\] ウィンドウに単一の行の編集など\)。|  
|IHF\_FORCECOMMITTOCONTEXT|このフラグが設定されコンテキスト バッファーを更新する必要がある場合ホストは続行するに無視するコンテキスト バッファーおよび編集の読み取り専用フラグを有効にします。|  
|IHF\_OVERTYPE|編集が上書き入力モードで \(サブジェクト\) またはコンテキストにする必要があります。|  
  
#### IVsIntellisenseHost.BeforeCompletorCommit と IVsIntellisenseHost.AfterCompletorCommit  
 これらのメソッドはコールバックの前処理後処理の完了時にウィンドウでテキストがコミットされる前に呼び出されます。  
  
#### IVsIntellisenseCompletor  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor> のインターフェイスは統合開発環境で使用される標準の完了時にウィンドウの共同作成できるバージョンです \(IDE\)。  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> のすべてのインターフェイスがこの completor のインターフェイスを使用するとIntelliSense を実行できます。  
  
## 参照  
 <xref:Microsoft.VisualStudio.TextManager.Interop>