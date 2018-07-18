---
title: 従来の言語サービスでのアウトライン |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b899f53ba6b2a0b58997cc51a83a0d9ca8480e63
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135653"
---
# <a name="outlining-in-a-legacy-language-service"></a>従来の言語サービスでのアウトライン
アウトライン表示できるようになります概要またはアウトラインに複雑なプログラムを折りたたみます。 たとえば、c# ですべてのメソッドを折りたためるメソッド シグネチャのみを示す 1 つの行にします。 さらに、構造体とクラスは、構造体とクラス名のみを表示のために折りたたむことができます。 1 つのメソッドの内部に複雑なロジックを折りたためるなどのステートメントの最初の行だけを表示することによって、全体的なフローを表示する`foreach`、 `if`、および`while`です。  
  
 レガシ言語サービスは、VSPackage の一部として実装されますが、MEF 拡張機能を使用する言語サービスの機能を実装する新しい方法です。 詳細については、次を参照してください。[チュートリアル: アウトライン](../../extensibility/walkthrough-outlining.md)です。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
## <a name="enabling-support-for-outlining"></a>アウトライン表示のサポートを有効にします。  
 `AutoOutlining`レジストリ エントリが 1 に設定すると、自動アウトライン表示を有効にします。 ファイルが読み込まれるまたは非表示の領域を識別し、アウトラインの記号を表示するために変更されたときに、ソース全体の解析を設定自動アウトライン表示します。 アウトライン表示制御することも手動でユーザーがします。  
  
 値、`AutoOutlining`でレジストリ エントリを取得できます、<xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A>プロパティを<xref:Microsoft.VisualStudio.Package.LanguagePreferences>クラスです。 `AutoOutlining`で名前付きパラメーターをレジストリ エントリを初期化することができます、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>属性 (を参照してください[レガシ言語サービスを登録する](../../extensibility/internals/registering-a-legacy-language-service1.md)詳細)。  
  
## <a name="the-hidden-region"></a>非表示の領域  
 アウトラインを提供するに言語サービスは非表示の領域をサポートする必要があります。 これらは、展開または折りたたむことができますをテキストの範囲です。 中かっこなどの標準の言語記号またはカスタムのシンボルによって非表示の領域を区切ることができます。 たとえば、C# の場合は、 `#region` / `#endregion`を非表示の領域を取り出すためペア。  
  
 非表示の領域として公開されている非表示の領域マネージャーによって管理されている、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>インターフェイスです。  
  
 アウトラインの非表示領域を使用して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion>インターフェイスし、非表示の領域、現在の表示状態およびスパンが折りたたまれている場合に表示されるバナーのスパンが含まれています。  
  
 言語サービス パーサーを使用して、<xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A>メソッドを非表示の領域の既定の動作を持つ新しい非表示領域を追加するときに、<xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A>メソッドでは、アウトラインの動作と外観をカスタマイズすることができます。 非表示の領域が非表示の領域のセッションに与えられた後[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]言語サービスの非表示の領域を管理します。  
  
 非表示の領域を変更すると、非表示の領域のセッションが破棄される時点を決定する必要がある場合、または特定の非表示の領域が表示されていることを確認する必要があります。クラスを派生する必要があります、<xref:Microsoft.VisualStudio.Package.Source>クラスし、適切なメソッドをオーバーライド<xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>、 <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>、および<xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>、それぞれします。  
  
### <a name="example"></a>例  
 中かっこのすべてのペアの非表示の領域を作成する簡単な例を次に示します。 これと見なされ、言語に中かっこの一致が用意されている、照合するかっこが含まれている、少なくとも、中かっこには ({および})。 この方法は、わかりやすくするためだけです。 内のケースの完全な処理には、完全な実装<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>です。 この例では、設定する方法も示しています、<xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A>を優先する`true`一時的にします。 代わりを指定し、`AutoOutlining`という名前のパラメーター、`ProvideLanguageServiceAttribute`言語パッケージ内の属性です。  
  
 この例では、c# のコメントや文字列リテラルの規則を使用します。  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
  
    public class MyLanguageService : LanguageService  
    {  
        private LanguagePreferences m_preferences;  
  
        public override LanguagePreferences  GetLanguagePreferences()  
        {  
            if (m_preferences == null)  
            {  
                m_preferences = new LanguagePreferences(this.Site,  
                                                        typeof(MyLanguageService).GUID,  
                                                        Name);  
                m_preferences.Init();  
                // Temporarily enabled auto-outlining  
                m_preferences.AutoOutlining = true;  
            }  
            return m_preferences;  
        }  
  
        public override AuthoringScope  ParseSource(ParseRequest req)  
        {  
            Source source = (Source) this.GetSource(req.FileName);  
            switch (req.Reason)  
            {  
               case ParseReason.HighlightBraces:  
               case ParseReason.MatchBraces:  
               case ParseReason.MemberSelectAndHighlightBraces:  
                  if (source.Braces != null)  
                  {  
                      foreach (TextSpan[] brace in source.Braces)  
                      {  
                         if (brace.Length == 2)  
                         {  
                             if (req.Sink.HiddenRegions == true   
                                   && source.GetText(brace[0]).Equals("{")   
                                   && source.GetText(brace[1]).Equals("}"))  
                             {  
                                //construct a TextSpan of everything between the braces  
                                TextSpan hideSpan = new TextSpan();  
                                hideSpan.iStartIndex = brace[0].iStartIndex;  
                                hideSpan.iStartLine = brace[0].iStartLine;  
                                hideSpan.iEndIndex = brace[1].iEndIndex;  
                                hideSpan.iEndLine = brace[1].iEndLine;  
                                req.Sink.ProcessHiddenRegions = true;  
                                req.Sink.AddHiddenRegion(hideSpan);  
                             }  
                             req.Sink.MatchPair(brace[0], brace[1], 1);  
                         }  
                         else if (brace.Length >= 3)  
                             req.Sink.MatchTriple(brace[0], brace[1], brace[2], 1);  
                  }  
        }  
                   break;  
               default:  
                   break;  
      }  
            // Must always return a valid AuthoringScope object.  
            return new MyAuthoringScope();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [レガシ言語サービス機能](../../extensibility/internals/legacy-language-service-features1.md)   
 [レガシ言語サービスを登録します。](../../extensibility/internals/registering-a-legacy-language-service1.md)