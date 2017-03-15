---
title: "レガシ言語サービス内のコメント行のコード | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コメント、言語サービス [マネージ パッケージ フレームワーク] でのサポート"
  - "コードをコメント化言語サービス [マネージ パッケージ framework]"
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# レガシ言語サービス内のコメント行のコード
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

プログラミング言語には通常注釈したりコード コメント方法を示します。  コメントはコードに関する追加情報を提供するがでコンパイルされない解釈時には無視されますテキストのセクション。  
  
 マネージ パッケージ フレームワーク \(MPF\) クラスコメントを保持しuncommenting 選択したテキストをサポートします。  
  
## コメントのスタイル  
 コメントの 2 個の一般的なスタイルです :  
  
1.  単一行コメントがある場合に行のコメント。  
  
2.  コメントを複数行もコメントをブロックします。  
  
 ブロックのコメントに開始文字と終了文字の両方がありますが行のコメントには開始文字 \(文字があります。  たとえばC\#\/\/ の行にコメントの開始および \/\* ブロックのコメントの先頭および末尾での \*\/。  
  
 ユーザーが  **編集**  のコマンド  **選択範囲のコメント**  を選択すると\>\] メニューの \[ENT2ENT は <xref:Microsoft.VisualStudio.Package.Source> クラスの <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> のメソッドはコマンド ルーティングされます。  ユーザーがコマンド  **選択範囲のコメントを解除**  を選択するとそのコマンドは <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> のメソッドにルーティングされます。  
  
## サポート コード コメント  
 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> の `EnableCommenting` の名前付きパラメーターによって言語サービスのサポートのコード コメントを使用できます。  これは <xref:Microsoft.VisualStudio.Package.LanguagePreferences> クラスの <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> のプロパティを設定します。  設定の言語 servicce の機能の詳細については[言語サービスを登録します。](../../extensibility/internals/registering-a-legacy-language-service1.md) を参照してください。  
  
 また言語のコメント文字を含む <xref:Microsoft.VisualStudio.Package.CommentInfo> の構造を返すように <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> のメソッドをオーバーライドする必要があります。  C\# 形式の行のコメント文字が既定値です。  
  
### 例  
 <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> のメソッドの実装例を次に示します。  
  
```c#  
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
  
## 参照  
 [従来の言語サービスの機能](../../extensibility/internals/legacy-language-service-features1.md)   
 [言語サービスを登録します。](../../extensibility/internals/registering-a-legacy-language-service1.md)