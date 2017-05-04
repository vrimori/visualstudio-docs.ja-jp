---
title: "サーバー上のドキュメント内のデータへのアクセス | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "データ [Visual Studio での Office 開発], アクセス (サーバーで)"
  - "データ アクセス [Visual Studio での Office 開発]"
ms.assetid: 14a42e96-ed2f-48a1-a0c0-e19f9eba4956
caps.latest.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 31
---
# サーバー上のドキュメント内のデータへのアクセス
  Microsoft Office Word または Microsoft Office Excel のオブジェクト モデルを使用しなくても、ドキュメント レベルのカスタマイズ内のデータに対してプログラムを作成できます。  これは、Word または Excel がインストールされていないサーバー上のドキュメントに含まれているデータにアクセスできることを意味します。  たとえば、\([!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] ページ内の\) サーバー上のコードは、ドキュメント内のデータをカスタマイズし、カスタマイズされたドキュメントをエンド ユーザーに送信できます。  エンド ユーザーがドキュメントを開くと、ソリューション アセンブリのデータ バインディング コードが、カスタマイズされたデータをドキュメントにバインドします。  これが可能なのは、ドキュメント内のデータがユーザー インターフェイスから切り離されているためです。  詳細については、「[ドキュメント レベルのカスタマイズのキャッシュ データ](../vsto/cached-data-in-document-level-customizations.md)」を参照してください。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## サーバー上で使用するデータのキャッシュ  
 ドキュメント内のデータ オブジェクトをキャッシュするには、デザイン時にそのオブジェクトを <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 属性でマークするか、または実行時にホスト項目の `StartCaching` メソッドを使用します。  ドキュメント内のデータ オブジェクトをキャッシュするとき、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] は、ドキュメントに格納されている XML 文字列にオブジェクトをシリアル化します。  オブジェクトをキャッシュするには、オブジェクトが特定の要件を満たしている必要があります。  詳細については、「[キャッシュされたデータ](../vsto/caching-data.md)」を参照してください。  
  
 サーバー側のコードは、データ キャッシュ内の任意のデータ オブジェクトを操作できます。  キャッシュされたデータ インスタンスにバインドされているコントロールはユーザー インターフェイスに同期しており、データに加えられるサーバー側のすべての変更は、クライアント上でドキュメントを開くときに自動的に反映されます。  
  
## キャッシュ内のデータへのアクセス  
 コンソール アプリケーション、Windows フォーム アプリケーション、Web ページなど、Office 以外のアプリケーションからキャッシュ内のデータにアクセスできます。  キャッシュされたデータにアクセスするアプリケーションは、完全に信頼されている必要があります。部分信頼の Web アプリケーションは、Office ドキュメントにキャッシュされたデータを挿入、取得、または変更できません。  
  
 データ キャッシュには、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> クラスの <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> プロパティによって公開されるコレクションの階層からアクセスできます。  
  
-   <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> プロパティは、ドキュメント レベルのカスタマイズのキャッシュされたすべてのデータを含む <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> を返します。  
  
-   各 <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> には、1 つ以上の <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> オブジェクトが含まれます。  <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> には、1 つのクラス内で定義されている、キャッシュされたデータ オブジェクトがすべて含まれます。  
  
-   各 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> には、1 つ以上の <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> オブジェクトが含まれます。  <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> は、1 つのキャッシュされたデータ オブジェクトを表します。  
  
 次のコード例は、Excel ブック プロジェクトの `Sheet1` クラス内のキャッシュされた文字列にアクセスする方法を示しています。  この例は、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> メソッドのトピックで提供されているコード例の一部分です。  
  
 [!code-csharp[Trin_ServerDocument#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ServerDocument/CS/Form1.cs#12)]
 [!code-vb[Trin_ServerDocument#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ServerDocument/VB/Form1.vb#12)]  
  
## キャッシュ内のデータの変更  
 キャッシュされたデータ オブジェクトを変更するには、通常、次の操作を行います。  
  
1.  キャッシュされたオブジェクトの XML 表現をオブジェクトの新しいインスタンスに逆シリアル化します。  XML にアクセスするには、キャッシュされたデータ オブジェクトを表す <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> の <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> プロパティを使用します。  
  
2.  このコピーに対して変更を加えます。  
  
3.  次のいずれかの方法を使用して、変更を加えたオブジェクトをデータ キャッシュにシリアル化します。  
  
    -   変更を自動的にシリアル化する場合は、<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> メソッドを使います。  このメソッドでは、データ キャッシュ内の <xref:System.Data.DataSet>、<xref:System.Data.DataTable>、および型指定されたデータセット オブジェクトをシリアル化するために **DiffGram** 形式を使用します。  **DiffGram** 形式により、オフライン ドキュメントのデータ キャッシュに対する変更がサーバーに正しく送信されるようになります。  
  
    -   キャッシュされたデータの変更に対して独自のシリアル化を実行する場合は、<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> プロパティに直接書き込むことができます。  <xref:System.Data.Common.DataAdapter> を使用し、<xref:System.Data.DataSet>、<xref:System.Data.DataTable>、または型指定されたデータセット内のデータに対して行われた変更でデータベースを更新する場合は、**DiffGram** 形式を指定します。  それ以外の場合は、既存の行を変更するのではなく新しい行を追加することによって、<xref:System.Data.Common.DataAdapter> がデータベースを更新します。  
  
### 現在の値を逆シリアル化せずにデータを変更する  
 状況に応じて、現在の値を最初に逆シリアル化せずにキャッシュされたオブジェクトの値を変更することが必要になる場合があります。  たとえば、単純型 \(たとえば文字列や整数\) のオブジェクトの値を変更する場合やサーバー上のドキュメントのキャッシュされた <xref:System.Data.DataSet> を初期化する場合に、この操作を行います。  この場合、キャッシュされたオブジェクトの現在の値を最初に逆シリアル化することなく <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> メソッドを使用できます。  
  
 次のコード例は、Excel ブック プロジェクトの `Sheet1` クラス内のキャッシュされた文字列の値を変更する方法を示しています。  この例は、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> メソッドのトピックで提供されているコード例の一部分です。  
  
 [!code-csharp[Trin_ServerDocument#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ServerDocument/CS/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ServerDocument/VB/Form1.vb#11)]  
  
### データ キャッシュ内の null 値の変更  
 データ キャッシュは、ドキュメントを保存するときおよび閉じるときに **null** 値を含むオブジェクトを格納しません。  この制限から、キャッシュされたデータを変更すると、次のような動作が発生します。  
  
-   データ キャッシュ内のいずれかのオブジェクトを **null** 値に設定した場合、ドキュメントを開いたときにデータ キャッシュ内のすべてのオブジェクトが自動的に **null** に設定され、ドキュメントを保存したときおよび閉じたときにデータ キャッシュ全体が消去されます。  つまり、キャッシュされたすべてのオブジェクトがデータ キャッシュから削除され、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> コレクションが空になります。  
  
-   データ キャッシュ内の **null** オブジェクトを使用してソリューションをビルドし、ドキュメントが初めて開かれる前に <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> クラスを使用してこれらのオブジェクトを初期化する場合は、データ キャッシュ内のすべてのオブジェクトを初期化する必要があります。  一部のオブジェクトのみを初期化した場合、ドキュメントを開いたときにすべてのオブジェクトが **null** に設定され、ドキュメントを保存したときおよび閉じたときにデータ キャッシュ全体が消去されます。  
  
## キャッシュ内の型指定されたデータセットへのアクセス  
 Office ソリューションと、Windows フォーム アプリケーションや [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] プロジェクトなどの Office 以外のアプリケーションの両方から、型指定されたデータセット内のデータにアクセスする場合は、両方のプロジェクトで参照される各アセンブリで型指定されたデータセットを定義する必要があります。  **データ ソース構成ウィザード**または**データセット デザイナー**を使用して、型指定されたデータセットを各プロジェクトに追加すると、.NET Framework では、2 つのプロジェクト内の型指定されたデータセットの型が異なっていると見なされます。  型指定されたデータセットの作成の詳細については、「[方法 : 型指定されたデータセットを作成する](../Topic/Creating%20and%20configuring%20datasets%20in%20Visual%20Studio.md)」を参照してください。  
  
## 参照  
 [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md)   
 [ドキュメント レベルのカスタマイズのキャッシュ データ](../vsto/cached-data-in-document-level-customizations.md)  
  
  