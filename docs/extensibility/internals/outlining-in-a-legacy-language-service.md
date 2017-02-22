---
title: "従来の言語サービスでのアウトライン | Microsoft Docs"
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
  - "アウトライン"
  - "アウトライン表示言語サービス [マネージ パッケージ framework]"
  - "アウトライン、言語サービス [マネージ パッケージ フレームワーク] でのサポート"
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# 従来の言語サービスでのアウトライン
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

アウトライン表示できるようになります、概要やアウトラインに複雑なプログラムを折りたたみます。 たとえば、C\# の場合は、すべてのメソッドをメソッド署名のみを示す 1 つの行に縮小ことができます。 さらに、構造体とクラスは、構造体とクラス名のみを表示するために折りたたむことができます。 1 つのメソッド内の複雑なロジックを折りたためるなどのステートメントの最初の行のみを表示することによって、全体的な流れを表示する `foreach`, 、`if`, 、および `while`です。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は、MEF の拡張機能を使用します。 詳細については、次を参照してください。 [チュートリアル: アウトラインの中止\]](../../extensibility/walkthrough-outlining.md)します。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く始めることをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
## アウトライン表示のサポートを有効にします。  
 `AutoOutlining` 自動アウトライン表示を有効にするレジストリ エントリが 1 に設定します。 ファイルが読み込まれるか非表示の領域を特定し、\[アウトラインの記号を表示するために変更をソース全体の解析を設定自動アウトライン表示します。 アウトライン表示制御することも手動でユーザーがいます。  
  
 値、 `AutoOutlining` でレジストリ エントリを取得できます、 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> プロパティを <xref:Microsoft.VisualStudio.Package.LanguagePreferences> クラスです。`AutoOutlining` で名前付きパラメーターをレジストリ エントリを初期化すること、 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 属性 \(を参照してください [言語サービスを登録します。](../../extensibility/internals/registering-a-legacy-language-service1.md) 詳細\)。  
  
## 非表示の領域  
 アウトラインを提供するには、言語サービスは非表示の領域をサポートする必要があります。 これらは、展開または折りたたまれているテキストの範囲です。 非表示の領域は、中かっこなどの標準言語記号またはカスタムの記号で区切ることができます。 たとえば、c\# では、 `#region`\/`#endregion` を非表示の領域を区切るペアです。  
  
 非表示の領域として公開されている非表示の領域マネージャーによって管理されている、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> インターフェイスです。  
  
 アウトラインの非表示の領域を使用して、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> インターフェイスし、非表示の領域、現在の表示状態と期間が折りたたまれているときに表示されるバナーの範囲が含まれています。  
  
 言語サービス パーサーを使用して、 <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> メソッドを非表示の領域の既定の動作と新しい非表示の領域を追加するときに、 <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> メソッドでは、アウトラインの動作と外観をカスタマイズすることができます。 非表示の領域を非表示の領域のセッションに指定 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 言語サービスの非表示の領域を管理します。  
  
 非表示の領域を変更すると、非表示の領域のセッションを破棄するかを決める必要がある場合、または特定の非表示の領域が表示されるかどうかを確認する必要があります。クラスを派生する必要があります、 <xref:Microsoft.VisualStudio.Package.Source> クラスし、適切なメソッドをオーバーライド <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, 、<xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>, 、および <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>, 、それぞれします。  
  
### 例  
 中かっこのペアはすべての非表示の領域を作成する簡単な例を次に示します。 想定され、言語に中かっこの一致が用意されていると照合するために中かっこが含まれている、少なくとも、中かっこには \({および}\)。 この方法は、説明のためには。 内のケースの完全な処理を完全に実装が必要があります <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>します。 この例では、設定する方法も示しています、 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> を優先する `true` 一時的にします。 代わりを指定し、 `AutoOutlining` 名前付きパラメーター、 `ProvideLanguageServiceAttribute` 言語パッケージ内の属性です。  
  
 この例では、c\# のコメント、文字列、およびリテラルの規則を使用します。  
  
```c#  
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
  
## 参照  
 [従来の言語サービスの機能](../../extensibility/internals/legacy-language-service-features1.md)   
 [言語サービスを登録します。](../../extensibility/internals/registering-a-legacy-language-service1.md)