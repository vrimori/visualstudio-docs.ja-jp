---
title: 従来の言語サービスでコードを再フォーマット |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b5361706e4dbb3c009de903a53cc78fcb7b93634
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547494"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>従来の言語サービスの再フォーマット コード
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[従来の言語サービスでのコードの再フォーマット](https://docs.microsoft.com/visualstudio/extensibility/internals/reformatting-code-in-a-legacy-language-service)します。  
  
[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]インデントおよび空白の使用を正規化することで、ソース コードを再フォーマットすることができます。 これには、挿入、スペースや各の行の先頭にあるタブを削除または線の間の新しい行を追加、またはタブまたはスペースをタブでスペースを置き換えることを含めることができます。  
  
> [!NOTE]
>  **注**挿入、または改行文字を削除することができますに影響を与えるブレークポイントとブックマークなどのマーカーが追加または削除のスペースまたはタブ マーカーは影響しません。  
  
 ユーザーが選択して、再フォーマット操作を開始できます**形式の選択**または**形式のドキュメント**から、 **[詳細設定]** メニューで、**編集**メニュー。 コード スニペットまたは特定の文字が挿入されると、再フォーマット操作をトリガーこともできます。 たとえば、(C#)、右中かっこを入力すると、適切なレベルに自動的にインデント一致する始めかっことかっこの間にあるすべてはできません。  
  
 ときに[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]送信、**形式の選択**または**ドキュメントのフォーマット**コマンド、言語サービスを<xref:Microsoft.VisualStudio.Package.ViewFilter>クラスが呼び出す、<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.Source>クラス。 オーバーライドする必要がありますを書式設定をサポートするために、<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>独自の書式設定コードのメソッドを指定します。  
  
## <a name="enabling-support-for-reformatting"></a>再フォーマットのサポートを有効にします。  
 書式設定をサポートするために、`EnableFormatSelection`のパラメーター、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>に設定する必要があります`true`VSPackage を登録するとします。 これにより設定、<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A>プロパティを`true`します。 <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A>メソッドは、このプロパティの値を返します。 True の場合、返された場合、<xref:Microsoft.VisualStudio.Package.ViewFilter>クラスが呼び出す、<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>します。  
  
## <a name="implementing-reformatting"></a>再フォーマットを実装します。  
 再フォーマットを実装するからクラスを派生する必要があります、<xref:Microsoft.VisualStudio.Package.Source>クラスし、オーバーライド、<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>メソッド。 <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>オブジェクトには、書式を設定するスパンがについて説明しますと、<xref:Microsoft.VisualStudio.Package.EditArray>スパンで加えられた編集を保持するオブジェクト。 このスパンはドキュメント全体であることに注意してください。 ただし、スパンに加えられた複数の変更である可能性がある、ので、すべての変更は 1 つのアクションで元に戻すことのようになります。 これを行うには、すべての変更をラップする<xref:Microsoft.VisualStudio.Package.CompoundAction>オブジェクト (このトピックの「"CompoundAction クラスを使用して"セクションを参照してください)。  
  
### <a name="example"></a>例  
 次の例は、スペースがある 1 つすべてのコンマの後に、選択範囲のコンマ、タブで後にかは、行の最後にしない限り、ようにします。 行の最後のコンマを削除した後は、末尾のスペースを実行します。 このメソッドを呼び出す方法を確認するには、このトピックの「the CompoundAction クラスを使用して」セクションを参照してください、<xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>メソッド。  
  
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
 すべての再フォーマット コードのセクションでは、1 つのアクションで元に戻すこと必要があります。 これを使用して、<xref:Microsoft.VisualStudio.Package.CompoundAction>クラス。 このクラスは、一連の単一の編集操作にテキスト バッファーの編集操作をラップします。  
  
### <a name="example"></a>例  
 使用する方法の例を次に示します、<xref:Microsoft.VisualStudio.Package.CompoundAction>クラス。 このトピックの例の"を実装するサポートの"の書式設定セクションの例を参照してください、`DoFormatting`メソッド。  
  
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
 [従来の言語サービスの特徴](../../extensibility/internals/legacy-language-service-features1.md)

