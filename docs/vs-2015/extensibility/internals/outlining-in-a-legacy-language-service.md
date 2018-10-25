---
title: 従来の言語サービスでのアウトライン |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 69ea15c814472303ffd3a0097e7e61777805d487
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263225"
---
# <a name="outlining-in-a-legacy-language-service"></a>従来の言語サービスのアウトライン
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

アウトライン表示できるようになります、概要やアウトラインに複雑なプログラムを折りたたみます。 たとえば、c# では、すべてのメソッドをメソッドのシグネチャのみを示す、1 行に折りたたむことが。 さらに、構造体とクラスは、構造体とクラス名のみを表示のために折りたたむことができます。 1 つのメソッド内で複雑なロジックをなどのステートメントの最初の行のみを表示することによって全体的な流れに折りたたむことができます`foreach`、 `if`、および`while`します。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は MEF 拡張機能を使用します。 詳細については、次を参照してください。[チュートリアル: アウトライン](../../extensibility/walkthrough-outlining.md)します。  
  
> [!NOTE]
>  新しいエディターの API をできるだけ早く使用を開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用することができます。  
  
## <a name="enabling-support-for-outlining"></a>アウトラインのサポートを有効にします。  
 `AutoOutlining`レジストリ エントリが 1 に設定すると、自動的なアウトラインを有効にします。 ファイルが読み込まれたまたは非表示の領域を特定し、アウトラインのグリフを表示するために変更されたときに、全体のソースの解析を設定自動アウトライン表示します。 アウトライン表示制御することも手動でユーザーがいます。  
  
 値、`AutoOutlining`でレジストリ エントリを取得できます、<xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A>プロパティを<xref:Microsoft.VisualStudio.Package.LanguagePreferences>クラス。 `AutoOutlining`で名前付きパラメーターをレジストリ エントリを初期化することができます、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>属性 (を参照してください[従来の言語サービスを登録する](../../extensibility/internals/registering-a-legacy-language-service1.md)詳細については)。  
  
## <a name="the-hidden-region"></a>非表示領域  
 アウトラインを提供するには、言語サービスは、非表示の領域をサポートする必要があります。 これらは、展開または折りたたまれているテキストの範囲です。 中かっこなどの標準の言語記号またはカスタムのシンボルは、非表示の領域を区切ることができます。 たとえば、c# では、 `#region` / `#endregion`を非表示の領域を区切るペア。  
  
 非表示の領域として公開される、非表示領域マネージャーによって管理されている、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>インターフェイス。  
  
 アウトラインの非表示の領域を使用して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion>インターフェイスを非表示の領域、現在の表示状態、および範囲が折りたたまれている場合に表示されるバナーのスパンを含めることができます。  
  
 言語サービス パーサーを使用して、<xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A>メソッドを非表示の領域の既定の動作を持つ新しい非表示領域を追加中に、<xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A>メソッドでは、アウトラインの動作と外観をカスタマイズできます。 非表示の領域は非表示の領域のセッションに付与されたら[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]言語サービスの非表示の領域を管理します。  
  
 非表示の領域を変更すると、非表示の領域のセッションが破棄される時期を決定する必要がある場合、または特定の非表示の領域が表示されるかどうかを確認する必要があります。クラスを派生する必要があります、<xref:Microsoft.VisualStudio.Package.Source>クラスし、適切なメソッドをオーバーライド<xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>、 <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>、および<xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>、それぞれします。  
  
### <a name="example"></a>例  
 中かっこのすべてのペアの非表示の領域の作成の簡略化された例を次に示します。 見なされ、言語には、かっこの一致、一致する中かっこが含まれている、少なくとも、中かっこには ({および})。 この方法では、例示を目的としてのみです。 完全な実装の必要があります内のケースの完全な処理<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>します。 この例では、設定する方法も示しています、<xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A>を優先する`true`一時的にします。 指定する代替策は、`AutoOutlining`名前付きパラメーター、`ProvideLanguageServiceAttribute`言語パッケージ内の属性。  
  
 この例では、c# コメント、文字列、およびリテラルの規則を使用します。  
  
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
 [従来の言語サービスの機能](../../extensibility/internals/legacy-language-service-features1.md)   
 [従来の言語サービスの登録](../../extensibility/internals/registering-a-legacy-language-service1.md)

