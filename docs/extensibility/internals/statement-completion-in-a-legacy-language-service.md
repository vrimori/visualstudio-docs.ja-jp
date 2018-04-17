---
title: 従来の言語サービスで入力候補 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d76face8f43bcb428a9c3b997083f8299d332cc8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="statement-completion-in-a-legacy-language-service"></a>従来の言語サービスで入力候補
ステートメント入力候補は、する言語サービスやすく、言語のキーワードまたはコア エディターに入力が開始されている要素を終了するプロセスです。 このトピックでは、ステートメント入力候補のしくみと、言語サービスに実装する方法について説明します。  
  
 レガシ言語サービスは、VSPackage の一部として実装されますが、MEF 拡張機能を使用する言語サービスの機能を実装する新しい方法です。 ステートメント入力候補を実装する新しい方法の詳細についてを参照してください。[チュートリアル: ステートメント入力候補を表示する](../../extensibility/walkthrough-displaying-statement-completion.md)です。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
## <a name="implementing-statement-completion"></a>ステートメント入力候補を実装します。  
 コア エディターでは、ステートメント入力候補には、対話形式より簡単にして、コードを簡単に作成される特別な UI がアクティブにします。 ステートメント入力候補は、表示することによって関連するオブジェクトまたはクラスは、必要に応じて、これを特定の要素を覚えておかなくてまたはヘルプの参照トピックで検索することにより回避するのに役立ちます。  
  
 ステートメント入力候補を実装するのが解析でき、ステートメント入力候補トリガーが、言語に必要です。 たとえば、[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]ドット (.) 演算子を使用して中[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]矢印を使用して (->) 演算子。 言語サービスは、1 つ以上のトリガーを使用して、ステートメント入力候補を開始します。 これらのトリガーは、コマンドのフィルターでプログラムを作成します。  
  
## <a name="command-filters-and-triggers"></a>コマンドのフィルターとトリガー  
 コマンドのフィルターは、トリガーやトリガーの発生を途中受信します。 ビューには、コマンドのフィルターを追加するには、実装、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイスし、呼び出すことによって、ビューにアタッチ、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>メソッドです。 同じコマンド フィルターを使用することができます (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) に、ステートメント入力候補、エラー マーカー、およびメソッドのヒントなど、言語サービスのすべての側面にします。 詳細については、次を参照してください。[レガシ言語サービス コマンドの傍受](../../extensibility/internals/intercepting-legacy-language-service-commands.md)です。  
  
 トリガーがエディターで入力されている場合: テキスト バッファーでは具体的には、-、言語サービスを呼び出します、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>メソッド。 これにより、ユーザーは、ステートメント入力候補の候補からを選択できるように、UI を表示するエディターです。 このメソッドでは、実装する必要があります<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>と<xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags>パラメーターとしてフラグ。 スクロール ボックスの一覧にコンプリート項目の一覧が表示されます。 ユーザーが入力を続ける、最新の文字に最も近い入力を反映するように、リスト ボックス内の選択項目が更新されます。 コア エディターは、ステートメント入力候補の UI を実装が言語サービスを実装する必要があります、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>ステートメントの候補コンプリート項目のセットを定義するインターフェイスです。  
  
## <a name="see-also"></a>関連項目  
 [従来の言語サービスのコマンドの受信](../../extensibility/internals/intercepting-legacy-language-service-commands.md)