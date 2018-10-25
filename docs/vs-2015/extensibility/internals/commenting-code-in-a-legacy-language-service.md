---
title: 従来の言語サービスでのコメント コード |Microsoft Docs
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
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d4b955879380166aae7d9a8e210ac7d5e53f882f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873475"
---
# <a name="commenting-code-in-a-legacy-language-service"></a>従来の言語サービスのコメント コード
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

プログラミング言語は、通常の注釈を設定するか、コードをコメントするための手段を提供します。 コメントは、コードに関する追加情報を提供しますが、コンパイルまたは解釈中に無視されるテキストのセクションです。  
  
 マネージ パッケージ フレームワーク (MPF) クラスは、選択したテキストをコメント化とコメント解除のサポートを提供します。  
  
## <a name="comment-styles"></a>コメントのスタイル  
 コメントの 2 つの一般的なスタイルがあります。  
  
1. 行のコメントを 1 行にコメントがあります。  
  
2. ブロックのコメント、コメントが複数の行を含めることができます。  
  
   行のコメントは、通常、開始文字 (文字)、ブロックのコメントの中に開始と終了の両方の文字があります。 たとえば、c# の場合は、行のコメントから始まります//、ブロックのコメントの始まりと/* で終わる\*/。  
  
   ユーザーがコマンドを選択すると**選択範囲のコメント**から、**編集** -> **詳細** メニューにコマンドがルーティングされます、<xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A>メソッドを<xref:Microsoft.VisualStudio.Package.Source>クラス。 ユーザーがコマンドを選択すると**選択範囲のコメントを解除します**にルーティングは、コマンド、<xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A>メソッド。  
  
## <a name="supporting-code-comments"></a>コードのコメントをサポートしています。  
 言語サービスのサポート コード コメントがあることができます、`EnableCommenting`名前付きのパラメーター、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>します。 これにより設定、<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A>のプロパティ、<xref:Microsoft.VisualStudio.Package.LanguagePreferences>クラス。 サービス機能の言語を設定する方法についての詳細については、次を参照してください。[従来の言語サービスを登録する](../../extensibility/internals/registering-a-legacy-language-service1.md))。  
  
 オーバーライドすることも必要があります、<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>を返すメソッドを<xref:Microsoft.VisualStudio.Package.CommentInfo>言語のコメント文字を含む構造体。 C#-行のコメント文字のスタイルは、既定値。  
  
### <a name="example"></a>例  
 実装例を次に示します、<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>メソッド。  
  
```csharp  
using Microsoft.VisualStudio.Package;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        public override CommentInfo GetCommentFormat() {  
            CommentInfo info = new CommentInfo();  
            info.LineStart       = "//";  
            info.BlockStart      = "/*";  
            info.BlockEnd        = "*/";  
            info.UseLineComments = true;  
            return info;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [従来の言語サービスの機能](../../extensibility/internals/legacy-language-service-features1.md)   
 [従来の言語サービスの登録](../../extensibility/internals/registering-a-legacy-language-service1.md)

