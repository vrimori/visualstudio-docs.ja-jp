---
title: データのキャッシュ |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], about caching data
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 094a4e6c639007fcf09ce28f0be2e398b8245858
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="caching-data"></a>キャッシュされたデータ
  ドキュメント レベル カスタマイズでデータ オブジェクトをキャッシュするには、データは、オフライン、または Microsoft Office Word または Microsoft Office Excel を開くことがなく、アクセスできるようにします。 オブジェクトをキャッシュするには、オブジェクトにデータ型を特定の要件を満たすことが必要です。 .NET Framework の多くの一般的なデータ型など、これらの要件を満たしている<xref:System.String>、 <xref:System.Data.DataSet>、および<xref:System.Data.DataTable>です。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 データ キャッシュにオブジェクトを追加する 2 つの方法があります。  
  
-   ソリューションのビルド時に、データ キャッシュにオブジェクトを追加するには、適用、<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>オブジェクトの宣言するための属性です。 詳細については、次を参照してください。[する方法: オフラインで使用またはサーバー上にデータをキャッシュ](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)です。  
  
-   実行時にデータ キャッシュにオブジェクトをプログラムで追加するには、使用、`StartCaching`メソッドのホスト項目など、`ThisDocument`または`ThisWorkbook`クラスです。 詳細については、次を参照してください。[する方法: Office ドキュメント内のデータ ソースをプログラムでキャッシュ](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)です。  
  
 データ キャッシュにオブジェクトを追加した後は、アクセスして、Word または Excel を起動しなくても、キャッシュされたデータを変更することができます。 詳細については、「 [サーバー上のドキュメント内のデータへのアクセス](../vsto/accessing-data-in-documents-on-the-server.md)」を参照してください。  
  
## <a name="requirements-for-data-objects-to-be-cached"></a>キャッシュに保存するデータ オブジェクトの要件  
 ソリューション内のデータ オブジェクトをキャッシュするには、オブジェクトは、これらの要件を満たす必要があります。  
  
-   読み取り/書き込みのパブリック フィールドまたは、ホスト項目のプロパティをなどで、`ThisDocument`または`ThisWorkbook`クラスです。  
  
-   インデクサーまたはパラメーター化された他のプロパティ。  
  
 さらに、データ オブジェクトがによってシリアル化可能にする必要があります、<xref:System.Xml.Serialization.XmlSerializer>クラスで、オブジェクトの型は、これらの特性を持つ必要があります。  
  
-   パブリック型であります。  
  
-   パラメーターなしのパブリック コンス トラクターを持ちます。  
  
-   追加のセキュリティ特権を必要とするコードを実行できません。  
  
-   読み取り/書き込みパブリックのプロパティ (その他のプロパティは無視されます) のみを公開します。  
  
-   多次元配列の (入れ子にされた配列が受け入れられます) を公開しません。  
  
-   プロパティやフィールドからインターフェイスを返しません。  
  
-   実装していません<xref:System.Collections.IDictionary>場合コレクション。  
  
 データ オブジェクトをキャッシュすると、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 、オブジェクトに格納されている XML 文字列をシリアル化、*カスタム XML 部分*ドキュメントにします。 詳細については、「 [Custom XML Parts Overview](../vsto/custom-xml-parts-overview.md)」を参照してください。  
  
## <a name="cached-data-size-limits"></a>キャッシュされたデータ サイズの制限  
 データ キャッシュ内の個別のオブジェクトのサイズと、ドキュメント内のデータ キャッシュに追加できるデータの総量をいくつかの制限があります。 これらの制限を超えると、データ キャッシュにデータを保存するときに、アプリケーション予期せず終了可能性があります。  
  
 これらの制限を避けるためには、次のガイドラインに従います。  
  
-   データ キャッシュには、10 MB を超える任意のオブジェクトを追加できません。  
  
-   1 つのドキュメント内のデータ キャッシュには、100 MB を超えるデータの合計を追加できません。  
  
 これらは、概算値です。 正確な制限は、使用可能な RAM および実行中のプロセス数など、いくつかの要因によって異なります。  
  
## <a name="controlling-the-behavior-of-cached-objects"></a>キャッシュされたオブジェクトの動作を制御します。  
 キャッシュされたオブジェクトの動作を制御することができますを実装する、<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>キャッシュされたオブジェクトの種類のインターフェイスです。 たとえば、オブジェクトが変更されたときにユーザーを通知する方法を制御する場合は、このインターフェイスを実装できます。 実装する方法を示すコード例について<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>を参照してください、`ControlCollection`ダイナミック コントロールのサンプルの Excel および Word で動的コントロールのサンプル クラス[Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)です。  
  
## <a name="persisting-changes-to-cached-data-in-password-protected-documents"></a>パスワードで保護されたドキュメントのキャッシュされたデータを永続化の変更  
 パスワードで保護されたドキュメント内のデータ オブジェクトをキャッシュする場合、キャッシュされたデータへの変更は保存されません。 2 つのメソッドをオーバーライドすることで、キャッシュされたデータに変更を保存できます。 ドキュメントを保存すると、保護が一時的に削除するこれらのメソッドをオーバーライドし、保存した後に保護を再度適用操作が完了しました。  
  
 詳細については、次を参照してください。[する方法: Password-Protected ドキュメントでキャッシュ データ](../vsto/how-to-cache-data-in-a-password-protected-document.md)です。  
  
## <a name="preventing-data-loss-when-adding-null-values-to-the-data-cache"></a>データ キャッシュに Null 値を追加するときにデータ損失の防止  
 データ キャッシュにオブジェクトを追加するときのすべてのキャッシュされたオブジェクトに初期化する必要ない**null**ドキュメントが保存され、終了するまでの値します。 キャッシュされたオブジェクトがある場合、 **null**ドキュメントを保存して閉じるときに、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]データ キャッシュから削除するすべてのキャッシュされたオブジェクトに自動的にします。  
  
 持つオブジェクトを追加する場合、 **null**値を使用して、データ キャッシュを<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>属性、デザイン時に使用することができます、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>ドキュメントが開かれる前に、キャッシュされたデータを初期化するためにクラスのオブジェクトします。 これは、Word または Excel のドキュメントは、エンドユーザーが開かれる前にインストールされていないサーバー上のキャッシュされたデータを初期化する場合に便利です。 詳細については、「 [サーバー上のドキュメント内のデータへのアクセス](../vsto/accessing-data-in-documents-on-the-server.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [方法: オフラインであるか、サーバーで使用するデータをキャッシュ](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [方法: Office ドキュメント内のデータ ソースをプログラムでキャッシュ](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [方法: パスワードで保護されたドキュメント内のデータをキャッシュします。](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [チュートリアル: キャッシュされたデータセットを使用したマスター/詳細関係の作成](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)  
  
  