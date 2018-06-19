---
title: 従来の言語サービス内のコードを再フォーマット |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 392afbafc2ce15dbf7ee347efdf24ce1f7fe2301
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133197"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>従来の言語サービス内のコードを再フォーマット

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]正規化のインデントおよび空白を使用して、ソース コードを再フォーマットすることができます。 これには、挿入や削除、スペースまたはタブの各行の先頭に、線の間の新しい行を追加するタブまたはタブを空白のスペースに置き換えてを含めることができます。  
  
>**注:** 挿入、または改行文字を削除することができますに影響を与えるブレークポイントとブックマークなどのマーカーが追加または削除のスペースまたはタブ マーカーは影響しません。  
  
ユーザーを選択して、再フォーマット操作を開始できます**形式の選択**または**ドキュメントのフォーマット**から、**詳細**メニューで、 **を編集**メニュー。 コード スニペットであるか、特定の文字が挿入されると、再フォーマット操作をトリガーもできます。 たとえば、C# の場合、右かっこを入力するときにすべて一致する始め中かっことかっこの間で適切なレベルに自動的にインデントではありません。
  
ときに[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]送信、**形式の選択**または**ドキュメントのフォーマット**コマンド言語サービスを<xref:Microsoft.VisualStudio.Package.ViewFilter>クラスの呼び出し、<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.Source>クラスです。 オーバーライドする必要がありますの書式設定をサポートするために、<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>独自の書式設定コードのメソッドを指定します。  
  
## <a name="enabling-support-for-reformatting"></a>再フォーマットのサポートを有効にします。  

書式指定をサポートするために、`EnableFormatSelection`のパラメーター、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>に設定する必要があります`true`VSPackage を登録するとします。 これにより設定、<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A>プロパティを`true`です。 <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A>メソッドは、このプロパティの値を返します。 True の場合、返された場合、<xref:Microsoft.VisualStudio.Package.ViewFilter>クラスの呼び出し、<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>です。  
  
## <a name="implementing-reformatting"></a>再フォーマットを実装します。

再フォーマットを実装するのからクラスを派生する必要があります、<xref:Microsoft.VisualStudio.Package.Source>クラスし、オーバーライド、<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>メソッドです。 <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>書式を設定する範囲を記述するオブジェクトと<xref:Microsoft.VisualStudio.Package.EditArray>オブジェクトが範囲で行われた編集を保持します。 このスパンでドキュメント全体があることに注意してください。 ただし、スパンに加えられた変更を複数である可能性があるため、すべての変更は 1 つのアクションで元に戻すことのようになります。 これを行うには、すべての変更をラップする<xref:Microsoft.VisualStudio.Package.CompoundAction>オブジェクト (このトピックのセクションの「CompoundAction クラスを使用して」を参照してください)。

### <a name="example"></a>例  

次の例では、スペースがある 1 つすべてのコンマの後の選択 で、コンマ、タブで後にまたは行の末尾にある場合を除きを保証します。 行の最後のコンマを削除した後は、末尾のスペースを確認します。 このメソッドを呼び出す方法を表示するには、このトピックの「CompoundAction クラスを使用して」セクションを参照して、<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>メソッドです。  

```csharp 
using Microsoft.VisualStudio.Package;  
using Microsoft VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        private void DoFormatting(EditArray mgr, TextSpan span)  
        {  
            // Make sure there is one space after every comma unless followed  
            // by a tab or comma is at end of line.  
            IVsTextLines pBuffer = GetTextLines();  
            if (pBuffer != null)  
            {  
                int    startIndex = span.iStartIndex;  
                int    endIndex   = 0;  
                string line       = "";  
                // Loop over all lines in span  
                for (int i = span.iStartLine; i <= span.iEndLine; i++)  
                {  
                    if (i < span.iEndLine)  
                    {  
                        pBuffer.GetLengthOfLine(i, out endIndex);  
                    }  
                    else  
                    {  
                        endIndex = span.iEndIndex;  
                    }  
                    pBuffer.GetLineText(i, startIndex, i, endIndex, out line);  
  
                    if (line.Length > 0)  
                    {  
                        int index = 0;  
                        // Loop over all commas in line  
                        while ((index = line.IndexOf(',', index)) != -1)  
                        {  
                            int spaceIndex = index + 1;  
                            // Determine how many spaces after comma  
                            while (spaceIndex < line.Length && line[spaceIndex] == ' ')  
                            {  
                                ++spaceIndex;  
                            }  
  
                            int      spaceCount      = spaceIndex - (index + 1);  
                            string   replacementText = " ";  
                            bool     fDoEdit         = true;  
                            TextSpan editTextSpan    = new TextSpan();  
  
                            editTextSpan.iStartLine  = i;  
                            editTextSpan.iEndLine    = i;  
                            editTextSpan.iStartIndex = index + 1;  
  
                            if (spaceIndex == line.Length)  
                            {  
                                if (spaceCount > 0)  
                                {  
                                    // Delete spaces after a comma at end of line  
                                    editTextSpan.iEndIndex = spaceIndex;  
                                    replacementText = "";  
                                }  
                                else  
                                {  
                                    // Otherwise, do not add spaces if comma is  
                                    // at end of line.  
                                    fDoEdit = false;  
                                }  
                            }  
                            else if (spaceCount == 0)  
                            {  
                                if (spaceIndex < line.Length && line[spaceIndex] == '\t')  
                                {  
                                    // Do not insert space if a tab follows  
                                    // a comma.  
                                    fDoEdit = false;  
                                }  
                                else  
                                {  
                                    // No space after comma so add a space.  
                                    editTextSpan.iEndIndex = index + 1;  
                                }  
                            }  
                            else if (spaceCount > 1)  
                            {  
                                // More than one space after comma, replace  
                                // with a single space.  
                                editTextSpan.iEndIndex = spaceIndex;  
                            }  
                            else  
                            {  
                                // Single space after a comma and not at end  
                                // of the line, leave it alone.  
                                fDoEdit = false;  
                            }  
                            if (fDoEdit)  
                            {  
                                // Add edit operation  
                                mgr.Add(new EditSpan(editTextSpan, replacementText));  
                            }  
                            index = spaceIndex;  
                        }  
                    }  
                    startIndex = 0; // All subsequent lines start at 0  
                }  
                // Apply all edits  
                mgr.ApplyEdits();  
            }  
        }  
    }  
}  
```  
  
## <a name="using-the-compoundaction-class"></a>CompoundAction クラスを使用します。  
 
すべての再フォーマット コードのセクションで行われると、1 つのアクションで元に戻すこと必要があります。 これを使用して、<xref:Microsoft.VisualStudio.Package.CompoundAction>クラスです。 このクラスは、一連の 1 つの編集操作にテキスト バッファーの編集操作をラップします。  
  
### <a name="example"></a>例

使用する方法の例をここでは、<xref:Microsoft.VisualStudio.Package.CompoundAction>クラスです。 「を実装するサポートの書式設定」セクションの例は、このトピックで例を参照して、`DoFormatting`メソッドです。  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        public override void ReformatSpan(EditArray mgr, TextSpan span)  
        {  
            string description = "Reformat code";  
            CompoundAction ca = new CompoundAction(this, description);  
            using (ca)  
            {  
                ca.FlushEditActions();      // Flush any pending edits  
                DoFormatting(mgr, span);    // Format the span  
            }  
        }  
    }  
}  
```  

## <a name="see-also"></a>関連項目

[レガシ言語サービス機能](legacy-language-service-features1.md)