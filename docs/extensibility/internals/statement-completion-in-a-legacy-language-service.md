---
title: 従来の言語サービスで入力候補 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0310f515a444d0ff68fe971463602c484763848b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54965680"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>従来の言語サービスでのステートメント入力補完
ステートメント入力候補は、言語サービスにより、ユーザーの言語のキーワードやコア エディターでの入力が開始要素を完了するプロセスです。 このトピックでは、ステートメント入力候補のしくみと、言語サービスで実装する方法について説明します。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は MEF 拡張機能を使用します。 ステートメント入力候補を実装する新しい方法の詳細についてを参照してください。[チュートリアル。ステートメント入力候補を表示する](../../extensibility/walkthrough-displaying-statement-completion.md)します。  
  
> [!NOTE]
>  新しいエディターの API をできるだけ早く使用を開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用することができます。  
  
## <a name="implementing-statement-completion"></a>ステートメント入力候補を実装します。  
 コア エディターでは、ステートメント入力候補より簡単に対話的に支援して、すばやくコードを記述する特別な UI がアクティブにします。 ステートメント入力候補は、表示することで関連するオブジェクトまたはクラスが必要なときを特定の要素を覚えておくか、ヘルプの参照トピックで確認することを回避するのに役立ちます。  
  
 ステートメント入力候補を実装するには、お使いの言語のステートメント入力候補トリガー、解析できる必要があります。 たとえば、[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]ドット (.) 演算子を使用して中に[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]矢印を使用して (->) 演算子。 言語サービスは、1 つ以上のトリガーを使用して、ステートメント入力候補を開始できます。 これらのトリガーは、コマンドのフィルターでプログラムを作成します。  
  
## <a name="command-filters-and-triggers"></a>コマンドのフィルターとトリガー  
 コマンドのフィルターは、トリガーやトリガーの発生をインターセプトします。 ビューには、コマンドのフィルターを追加するには、実装、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイスを呼び出すことによって、ビューにアタッチ、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>メソッド。 同じコマンド フィルターを使用することができます (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) のステートメント入力候補、エラー マーカー、およびメソッドのヒントなど、言語サービスのすべての側面です。 詳細については、次を参照してください。[レガシ言語サービス コマンドのインターセプト](../../extensibility/internals/intercepting-legacy-language-service-commands.md)します。  
  
 トリガーが、エディターに入力された場合、テキスト バッファーでは具体的には、-、言語サービスを呼び出して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>メソッド。 これにより、ステートメント入力候補の候補として、ユーザーが選択できるように、UI を起動するエディターです。 このメソッドでは、実装する必要があります<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>と<xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags>パラメーターとしてフラグします。 スクロール リスト ボックスに入力候補の項目の一覧が表示されます。 ユーザーは、入力は引き続き、最新の文字に最も近い一致が型指定を反映するように、リスト ボックス内の選択範囲が更新されます。 コア エディターには、ステートメント入力候補の UI が実装されていますが、言語サービスを実装する必要があります、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>一連のステートメント候補入力候補の項目を定義するインターフェイス。  
  
## <a name="see-also"></a>関連項目  
 [従来の言語サービスのコマンドの受信](../../extensibility/internals/intercepting-legacy-language-service-commands.md)