---
title: "従来の言語サービスでのステートメント入力候補 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ステートメント入力候補"
  - "言語サービスでは、ステートメント入力候補"
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 従来の言語サービスでのステートメント入力候補
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ステートメント入力候補は、言語サービスを使用してユーザーの言語のキーワードまたは起動コア エディターに入力である要素が終了するプロセスです。 このトピックでは、ステートメント入力候補のしくみと、言語サービスに実装する方法について説明します。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は、MEF の拡張機能を使用します。 ステートメント入力候補を実装する新しい方法の詳細を参照してください [チュートリアル: 候補の表示](../../extensibility/walkthrough-displaying-statement-completion.md)します。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く始めることをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
## ステートメント入力候補を実装します。  
 コア エディターでは、ステートメント入力候補には、対話形式より簡単にし、すばやくコードを記述する特殊な UI がアクティブにします。 ステートメント入力候補が表示することによって関連するオブジェクトまたはクラスが必要なときにこれを特定の要素を覚えておかなくてまたはヘルプ リファレンスのトピックで検索することにより、回避するのに役立ちます。  
  
 ステートメント入力候補を実装するのが解析でき、ステートメント入力候補トリガーが使用する言語に必要です。 たとえば、 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] ドット \(.\) を使用して 演算子、中に [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 矢印を使用して \(\-\>\) 演算子。 言語サービスは、1 つ以上のトリガーを使用して、ステートメント入力候補を開始します。 これらのトリガーは、コマンドのフィルターでプログラムを作成します。  
  
## コマンドのフィルターとトリガー  
 コマンドのフィルターは、トリガーやトリガーの発生をインターセプトします。 ビューには、コマンドのフィルターを追加するには、実装、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> インターフェイスを呼び出すことによって、ビューにアタッチ、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> メソッドです。 同じコマンド フィルターを使用することができます \(<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>\) ステートメント入力候補、エラー マーカー、およびメソッドのヒントなど、言語サービスのあらゆる側面にします。 詳細については、「[従来の言語サービスのコマンドを受信](../../extensibility/internals/intercepting-legacy-language-service-commands.md)」を参照してください。  
  
 トリガーがエディターに入力された場合、具体的には、テキスト バッファー\-言語サービスを呼び出します、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> メソッドです。 これにより、ようにするために、UI をユーザーがステートメント補完候補から選択できるエディターです。 このメソッドでは、実装する必要があります <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> と <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> パラメーターとしてフラグされます。 スクロール リスト ボックスに入力候補項目の一覧が表示されます。 ユーザーが入力を続ける、最新の文字に最も一致する入力を反映するように、リスト ボックス内の選択項目が更新されます。 コア エディターは、入力候補の UI を実装しますが、言語サービスを実装する必要があります、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> ステートメント候補コンプリート項目のセットを定義するインターフェイスです。  
  
## 参照  
 [従来の言語サービスのコマンドを受信](../../extensibility/internals/intercepting-legacy-language-service-commands.md)