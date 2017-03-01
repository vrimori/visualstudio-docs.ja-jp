---
title: "従来の言語サービス内のコードを再フォーマット |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 08d537f003279283509913d5f3d6aaa1bb1c4600
ms.openlocfilehash: d78fb976b3500a657d080634c6a041c218c3f1a1
ms.lasthandoff: 02/22/2017

---
# <a name="reformatting-code-in-a-legacy-language-service"></a>従来の言語サービス内のコードを再フォーマット

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]の使用、インデントおよび空白を正規化して、ソース コードを再フォーマットすることができます。 これには、挿入、スペースや各行の先頭にあるタブを削除または線の間の新しい行を追加、または空白をタブまたはタブを空白に置き換えてを含めることができます。  
  
>**注:**挿入、または改行文字を削除するには、ブレークポイントとブックマークなどのマーカー影響ことができますが、追加または削除のスペースまたはタブ マーカーは影響しません。  
  
ユーザーを選択して、再フォーマット操作を開始できます**形式の選択**または**ドキュメントのフォーマット**から、**詳細設定**メニューで、**編集**メニュー。 コード スニペットであるか、特定の文字が挿入されたときに、再フォーマット操作をトリガーもできます。 たとえば、C# の場合、右中かっこを入力すると対応する左中かっこと閉じる中かっこの間のすべては適切なレベルに自動的にインデントではありません。
  
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]送信、**形式の選択**または**ドキュメントのフォーマット**<xref:Microsoft.VisualStudio.Package.ViewFilter>クラスが<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A><xref:Microsoft.VisualStudio.Package.Source>クラス</xref:Microsoft.VisualStudio.Package.Source>のメソッド</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>を呼び出して</xref:Microsoft.VisualStudio.Package.ViewFilter>、言語サービスにコマンド オーバーライドする必要があります書式設定をサポートするために、<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>書式を独自のコードをメソッドおよび装置</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>。  
  
## <a name="enabling-support-for-reformatting"></a>再フォーマットのサポートを有効にします。  

書式設定をサポートするために、`EnableFormatSelection`のパラメーター、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>に設定する必要があります`true`VSPackage を登録するとします</xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>。 これにより設定、<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A>プロパティを`true`</xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A>。 <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A>メソッドは、このプロパティの値を返します</xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A>。 True を返したと<xref:Microsoft.VisualStudio.Package.ViewFilter>クラスを呼び出して<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>。</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A></xref:Microsoft.VisualStudio.Package.ViewFilter>場合  
  
## <a name="implementing-reformatting"></a>再フォーマットを実装します。

再フォーマットを実装するのには派生クラスを<xref:Microsoft.VisualStudio.Package.Source>クラスさせ、<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>メソッド</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A></xref:Microsoft.VisualStudio.Package.Source>。 <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>オブジェクトを書式設定して<xref:Microsoft.VisualStudio.Package.EditArray>、間隔に加えられた編集を保持するオブジェクト</xref:Microsoft.VisualStudio.Package.EditArray>を範囲の説明</xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> この範囲が文書全体にできることに注意してください。 ただし、スパンにに対する複数の変更をする可能性がありますが、ためすべての変更は&1; つのアクションで元に戻すことのようになります。 これを行うには、すべての変更をラップする<xref:Microsoft.VisualStudio.Package.CompoundAction>オブジェクト (このトピックの「クラスを使用して、CompoundAction」セクションを参照してください).</xref:Microsoft.VisualStudio.Package.CompoundAction>

### <a name="example"></a>例  

次の例では、スペースがある&1; つすべてのコンマの後に、選択範囲のコンマ、タブで後にまたは行の末尾にある場合を除きをようにします。 行の最後のコンマを削除した後は、末尾のスペースを確認します。 このメソッドを呼び出す方法を表示するには、このトピックで使用して、CompoundAction クラスに関するセクションを参照して、<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>メソッド</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>。  

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
 
すべての再フォーマット コードのセクションで行うには、一度の操作で元に戻せる状態必要があります。 これは<xref:Microsoft.VisualStudio.Package.CompoundAction>クラス</xref:Microsoft.VisualStudio.Package.CompoundAction>を使用して実現できます。 このクラスは、単一の編集操作に、テキスト バッファーでの編集操作のセットをラップします。  
  
### <a name="example"></a>例

<xref:Microsoft.VisualStudio.Package.CompoundAction>クラス</xref:Microsoft.VisualStudio.Package.CompoundAction>を使用する方法の例を次に示します このトピックの例については「を実装するサポートの書式設定」セクションの例を参照して、`DoFormatting`メソッドです。  
  
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

[従来の言語サービスの機能](legacy-language-service-features1.md)
