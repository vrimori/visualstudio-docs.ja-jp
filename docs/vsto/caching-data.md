---
title: "キャッシュされたデータ | Microsoft Docs"
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
  - "データ [Visual Studio での Office 開発], キャッシュ"
  - "データ キャッシュ [Visual Studio での Office 開発]"
  - "データ キャッシュ [Visual Studio での Office 開発], データ キャッシュの概要"
ms.assetid: 6f34251e-7d31-4f2b-ac17-42fd2837c626
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# キャッシュされたデータ
  \(Microsoft Office Word または Microsoft Office Excel を起動せず\) オフラインでデータにアクセスできるように、ドキュメント レベルのカスタマイズのデータ オブジェクトをキャッシュできます。  オブジェクトをキャッシュするには、オブジェクトのデータ型が特定の要件を満たす必要があります。  <xref:System.String>、<xref:System.Data.DataSet>、および <xref:System.Data.DataTable> など、.NET Framework の一般的なデータ型の多くは、以下に示す要件を満たしています。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 データ キャッシュにオブジェクトを追加するには 2 つの方法があります。  
  
-   ソリューションのビルド時にデータ キャッシュにオブジェクトを追加するには、オブジェクトの宣言に <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 属性を適用します。  詳細については、「[方法 : オフラインで使用するデータまたはサーバー上で使用するデータをキャッシュする](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)」を参照してください。  
  
-   実行時にプログラムでデータ キャッシュにオブジェクトを追加するには、ホスト項目の `StartCaching` メソッド \(`ThisDocument` クラスや `ThisWorkbook` クラスなど\) を使用します。  詳細については、「[方法 : Office ドキュメント内のデータ ソースをプログラムでキャッシュする](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)」を参照してください。  
  
 データ キャッシュにオブジェクトを追加すると、Word や Excel を起動せずに、キャッシュされたデータにアクセスしたり、キャッシュされたデータを変更したりできます。  詳細については、「[サーバー上のドキュメント内のデータへのアクセス](../vsto/accessing-data-in-documents-on-the-server.md)」を参照してください。  
  
## キャッシュできるデータ オブジェクトの要件  
 ソリューションのデータ オブジェクトをキャッシュするには、オブジェクトが以下の要件を満たす必要があります。  
  
-   `ThisDocument` クラスや `ThisWorkbook` クラスなど、ホスト項目の読み書き可能なパブリック フィールドまたはプロパティであること。  
  
-   インデクサーまたはその他のパラメーター化されたプロパティではないこと。  
  
 さらに、データ オブジェクトは <xref:System.Xml.Serialization.XmlSerializer> クラスによってシリアル化できる必要があります。これは、オブジェクトの型が次の特性を備えている必要があることを意味します。  
  
-   パブリック型であること。  
  
-   パラメーターを使用しないパブリック コンストラクターがあること。  
  
-   追加のセキュリティ特権を必要とするコードを実行しないこと。  
  
-   読み書き可能なパブリック プロパティのみを公開していること \(それ以外のプロパティは無視されます\)。  
  
-   多次元配列を公開していないこと \(入れ子になった配列は可\)。  
  
-   プロパティおよびフィールドからインターフェイスを返さないこと。  
  
-   コレクションの場合、<xref:System.Collections.IDictionary> を実装しないこと。  
  
 データ オブジェクトをキャッシュするとき、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] は、ドキュメントの*カスタム XML 部分*に格納されている XML 文字列にオブジェクトをシリアル化します。  詳細については、「[カスタム XML 部分の概要](../vsto/custom-xml-parts-overview.md)」を参照してください。  
  
## キャッシュされたデータのサイズ制限  
 ドキュメントのデータ キャッシュに追加できるデータの合計量と、データ キャッシュ内の個別のオブジェクトのサイズには、いくつかの制限があります。  これらの制限を超えた場合、データ キャッシュにデータが保存されたときにアプリケーションが予期せずに終了することがあります。  
  
 これらの制限を回避するには、以下のガイドラインに従います。  
  
-   データ キャッシュに 10 MB を超える大きさのオブジェクトを追加しない。  
  
-   単一ドキュメントのデータ キャッシュに合計量が 100 MB を超えるデータを追加しない。  
  
 これらは概算値です。  正確な制限値は、使用可能な RAM や実行プロセス数などのいくつかの要因によって決まります。  
  
## キャッシュされたオブジェクトの動作の制御  
 キャッシュされたオブジェクトの動作をより詳細に制御するには、キャッシュされたオブジェクトの型に <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> インターフェイスを実装します。  たとえば、このインターフェイスを実装して、オブジェクト変更時のユーザーへの通知を制御できます。  <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> を実装する方法を示すコード例については、「[Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)」の Excel のダイナミック コントロールのサンプルおよび Word のダイナミック コントロールのサンプルの `ControlCollection` クラスを参照してください。  
  
## パスワードで保護されたドキュメント内のキャッシュされたデータに加えられた変更の永続化  
 パスワードで保護されたドキュメントにデータ オブジェクトをキャッシュした場合、キャッシュされたデータへの変更は保存されません。  2 つのメソッドをオーバーライドすることによって、キャッシュされたデータへの変更を保存できます。  ドキュメントを保存するときにこれらのメソッドをオーバーライドして一時的に保護を解除し、保存操作が完了した後に保護を再適用します。  
  
 詳細については、「[方法 : パスワードで保護されたドキュメント内のデータをキャッシュする](../vsto/how-to-cache-data-in-a-password-protected-document.md)」を参照してください。  
  
## データ キャッシュに Null 値を追加するときのデータ損失の回避  
 データ キャッシュにオブジェクトを追加するとき、キャッシュされたすべてのオブジェクトは、ドキュメントを保存して閉じる前に **null** 以外の値に初期化される必要があります。  ドキュメントを保存して閉じるとき、キャッシュされたいずれかのオブジェクトに **null** 値が設定されていると、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] はデータ キャッシュから、キャッシュされたすべてのオブジェクトを自動的に削除します。  
  
 デザイン時に <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 属性を使用して、**null** 値を設定したオブジェクトをデータ キャッシュに追加した場合は、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> クラスを使用して、キャッシュされたデータ オブジェクトを初期化してからドキュメントを開くことができます。  この手法は、エンド ユーザーがドキュメントを開く前に、Word や Excel がインストールされていないサーバー上でキャッシュされたデータを初期化する場合に便利です。  詳細については、「[サーバー上のドキュメント内のデータへのアクセス](../vsto/accessing-data-in-documents-on-the-server.md)」を参照してください。  
  
## 参照  
 [方法 : オフラインで使用するデータまたはサーバー上で使用するデータをキャッシュする](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [方法 : Office ドキュメント内のデータ ソースをプログラムでキャッシュする](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [方法 : パスワードで保護されたドキュメント内のデータをキャッシュする](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [チュートリアル : キャッシュされたデータセットを使用したマスター&#47;詳細関係の作成](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)  
  
  