---
title: 従来の言語サービスでコメント コード |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5b573b464c26c3864cece697191cf03545ada779
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="commenting-code-in-a-legacy-language-service"></a>従来の言語サービスでコメント コード
プログラミング言語は、通常の注釈を設定するか、コードをコメントするための手段を提供します。 コメントは、コードに関する追加情報が、コンパイルまたは解釈中に無視されるテキストのセクションです。  
  
 マネージ パッケージ フレームワーク (MPF) クラスは、選択したテキストのコメントおよびコメントを解除のサポートを提供します。  
  
## <a name="comment-styles"></a>コメントのスタイル  
 コメントの 2 つの一般的なスタイルがあります。  
  
1.  1 行にコメントがここでは、行コメントです。  
  
2.  ブロックのコメント、コメントが複数の行を含めることがあります。  
  
 行のコメント通常開始文字 (or 文字) であるブロック コメント中に両方の開始と終了文字必要があります。 たとえば、C# の場合、行のコメントから始まります//、ブロックのコメントの始まりと/* で終わります\*/です。  
  
 ユーザーがコマンドを選択すると**選択範囲のコメント**から、**編集** -> **詳細**コマンドは、メニューにルーティング、<xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A>メソッドを<xref:Microsoft.VisualStudio.Package.Source>クラスです。 ユーザーがコマンドを選択すると**選択範囲のコメントを解除**、コマンドをルーティングする、<xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A>メソッドです。  
  
## <a name="supporting-code-comments"></a>コードのコメントをサポートします。  
 言語サービスのサポート コード コメントを持つことができます、`EnableCommenting`名前付きのパラメーター、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>です。 これにより設定、<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A>のプロパティ、<xref:Microsoft.VisualStudio.Package.LanguagePreferences>クラスです。 言語を設定するには、サービス機能の詳細については、次を参照してください。[レガシ言語サービスを登録する](../../extensibility/internals/registering-a-legacy-language-service1.md))。  
  
 上書きすることも必要があります、<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>を返すメソッドを<xref:Microsoft.VisualStudio.Package.CommentInfo>言語のコメント文字を含む構造体。 C# のスタイルの行のコメント文字は既定値です。  
  
### <a name="example"></a>例  
 実装例をここでは、<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>メソッドです。  
  
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
 [レガシ言語サービス機能](../../extensibility/internals/legacy-language-service-features1.md)   
 [レガシ言語サービスを登録します。](../../extensibility/internals/registering-a-legacy-language-service1.md)