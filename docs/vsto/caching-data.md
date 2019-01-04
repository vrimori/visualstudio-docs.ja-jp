---
title: キャッシュ データ
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], about caching data
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 66113dae824397f46829a539a016f452cedc0383
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53967256"
---
# <a name="cache-data"></a>キャッシュ データ
  データは、オフライン、または Microsoft Office Word または Microsoft Office Excel を開くことがなくアクセスできるように、ドキュメント レベル カスタマイズ内のデータ オブジェクトをキャッシュできます。 オブジェクトをキャッシュするには、オブジェクトのデータ型を特定の要件を満たす必要があります。 .NET Framework の多くの一般的なデータ型など、これらの要件を満たしている<xref:System.String>、 <xref:System.Data.DataSet>、および<xref:System.Data.DataTable>します。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 データ キャッシュにオブジェクトを追加する 2 つの方法はあります。  
  
- ソリューションのビルド時に、データ キャッシュにオブジェクトを追加するには、適用、<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>オブジェクトの宣言する属性します。 詳細については、「[方法 :オフラインか、サーバーで使用するデータをキャッシュ](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)します。  
  
- 実行時にデータ キャッシュにオブジェクトをプログラムで追加するには、使用、`StartCaching`メソッドのホスト項目など、`ThisDocument`または`ThisWorkbook`クラス。 詳細については、「[方法 :Office ドキュメント内のデータ ソースをプログラムでキャッシュ](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)します。  
  
  データ キャッシュにオブジェクトを追加した後は、アクセスして、Word または Excel を起動せず、キャッシュされたデータを変更することができます。 詳細については、次を参照してください。[サーバー上のドキュメント内のデータ アクセス](../vsto/accessing-data-in-documents-on-the-server.md)します。  
  
## <a name="requirements-for-data-objects-to-be-cached"></a>データ オブジェクトをキャッシュに保存するための要件  
 ソリューション内のデータ オブジェクトをキャッシュするには、オブジェクトは、これらの要件を満たす必要があります。  
  
- 読み取り/書き込みのパブリック フィールドまたは、ホスト項目のプロパティであるなど、`ThisDocument`または`ThisWorkbook`クラス。  
  
- インデクサーまたはその他のパラメーター化されたプロパティ。  
  
  さらに、データ オブジェクトがによってシリアル化可能にする必要があります、<xref:System.Xml.Serialization.XmlSerializer>クラスで、オブジェクトの型はこれらの特性である必要があります。  
  
- パブリック型であります。  
  
- パラメーターなしのパブリック コンス トラクターがあります。  
  
- 追加のセキュリティ特権を必要とするコードを実行できません。  
  
- 読み取り/書き込みパブリックのプロパティ (その他のプロパティは無視されます) のみを公開します。  
  
- (入れ子になった配列が受け入れられます)、多次元配列を公開しません。  
  
- プロパティやフィールドからインターフェイスを返しません。  
  
- 実装していません<xref:System.Collections.IDictionary>場合コレクション。  
  
  データ オブジェクトをキャッシュするときに、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 、オブジェクトに格納されている XML 文字列にシリアル化、*カスタム XML 部分*ドキュメント。 詳細については、次を参照してください。[カスタム XML 部分の概要](../vsto/custom-xml-parts-overview.md)します。  
  
## <a name="cached-data-size-limits"></a>キャッシュされたデータ サイズの制限  
 データ キャッシュ内の個別のオブジェクトのサイズと、ドキュメント内のデータ キャッシュに追加できるデータの総量をいくつかの制限があります。 これらの制限を超えると、データ キャッシュにデータが保存された場合に、アプリケーションが予期せず閉じることがあります。  
  
 これらの制限を避けるためには、次のガイドラインに従います。  
  
- データ キャッシュには、10 MB より大きい任意のオブジェクトを追加しないでください。  
  
- 1 つのドキュメント内のデータ キャッシュには、100 MB を超えるデータの合計を追加しないでください。  
  
  これらは、概算値です。 正確な制限は、使用可能な RAM および実行中のプロセス数など、いくつかの要因によって異なります。  
  
## <a name="control-the-behavior-of-cached-objects"></a>キャッシュされたオブジェクトの動作の制御  
 実装にキャッシュされたオブジェクトの動作を制御することができます、<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>キャッシュされたオブジェクトの種類のインターフェイス。 たとえば、オブジェクトが変更された場合に、ユーザーに通知する方法を制御する場合は、このインターフェイスを実装できます。 実装する方法を示すコード例について<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>を参照してください、`ControlCollection`動的コントロールのサンプルの Excel と Word で動的コントロールのサンプル クラス[Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)します。  
  
## <a name="persist-changes-to-cached-data-in-password-protected-documents"></a>パスワードで保護されたドキュメントでキャッシュされたデータへの変更を永続化します。  
 パスワードで保護されているドキュメント内のデータ オブジェクトをキャッシュする場合、キャッシュされたデータへの変更は保存されません。 2 つのメソッドをオーバーライドすることで、キャッシュされたデータに変更を保存できます。 ドキュメントが保存されると、保護を一時的に削除するこれらのメソッドをオーバーライドし、保存した後に保護を再度適用操作が完了しました。  
  
 詳細については、「[方法 :パスワードで保護されたドキュメント内のデータをキャッシュ](../vsto/how-to-cache-data-in-a-password-protected-document.md)します。  
  
## <a name="prevent-data-loss-when-adding-null-values-to-the-data-cache"></a>Null 値をデータ キャッシュに追加するときにデータ損失を防止します。  
 キャッシュされたオブジェクトのすべて必要があります以外に初期化するオブジェクトをデータ キャッシュに追加するときに**null**値、ドキュメントを保存して閉じる前にします。 任意のキャッシュされたオブジェクトがある場合、 **null**値、ドキュメントを保存して閉じられたときに、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]データ キャッシュから削除するすべてのキャッシュされたオブジェクトに自動的にします。  
  
 持つオブジェクトを追加する場合、 **null**値を使用して、データ キャッシュを<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>属性、デザイン時に使用することができます、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>ドキュメントが開かれる前に、キャッシュされたデータを初期化するためにクラスがオブジェクトします。 これは、Word または Excel ドキュメントをエンドユーザーが開く前にインストールされていないサーバー上のキャッシュされたデータの初期化に使用する場合に便利です。 詳細については、次を参照してください。[サーバー上のドキュメント内のデータ アクセス](../vsto/accessing-data-in-documents-on-the-server.md)します。  
  
## <a name="see-also"></a>関連項目  
 [方法: オフラインか、サーバーで使用するデータをキャッシュします。](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [方法: Office ドキュメント内のデータ ソースをプログラムでキャッシュします。](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [方法: パスワードで保護されたドキュメント内のキャッシュ データ](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [チュートリアル: キャッシュされたデータセットを使用したマスター/詳細関係を作成します。](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)  
