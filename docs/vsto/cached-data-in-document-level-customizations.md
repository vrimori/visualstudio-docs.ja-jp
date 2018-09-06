---
title: ドキュメント レベルのカスタマイズでキャッシュされたデータ
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data islands [Office development in Visual Studio]
- view [Office development in Visual Studio]
- caching data [Office development in Visual Studio], about caching data
- data caching [Office development in Visual Studio], about data caching
- data [Office development in Visual Studio], cache
- data [Office development in Visual Studio], document-level solutions
- document-level customizations [Office development in Visual Studio], data model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0710f196e6572cf6bc9851d8a765758fcb43326d
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673206"
---
# <a name="cached-data-in-document-level-customizations"></a>ドキュメント レベルのカスタマイズでキャッシュされたデータ
  ドキュメント レベルのカスタマイズの主な目的は、Office ドキュメントのビューからデータを分離します。 データは、数値やテキストなど、ドキュメントに格納されている情報を指します。 ビューは、ユーザー インターフェイスおよび Microsoft Office Word および Microsoft Office Excel のオブジェクト モデルを指します。  
  
 Visual Studio では、ドキュメント レベルのカスタマイズ ビューからデータを分離として埋め込まれるデータを有効にすると、*データ アイランド*も呼ばれ、*データ キャッシュ*します。 読み取りまたは Word または Excel を起動せずに直接データを変更できます。 これは、機能は、Microsoft Office がインストールされていないサーバー上のドキュメントのデータを変更する必要がある場合に便利です。 Word と Excel は、クライアントの環境での使用を意図していますサーバー上で実行される、設計されていません。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 ドキュメント レベルのカスタマイズの詳細については、次を参照してください。 [Office ソリューション開発の概要&#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md)と[のドキュメント レベル カスタマイズのアーキテクチャ](../vsto/architecture-of-document-level-customizations.md)します。  
  
## <a name="understand-the-cached-data-programming-model"></a>キャッシュされたデータのプログラミング モデルを理解します。  
 データ アイランドは、特定の要件を満たすソリューションのすべてのオブジェクトを含めることができます。 これらのオブジェクトを含める<xref:System.Data.DataSet>オブジェクト、<xref:System.Data.DataTable>オブジェクト、および他のオブジェクトをシリアル化できる、<xref:System.Xml.Serialization.XmlSerializer>クラス。 詳細については、次を参照してください。[データ キャッシュ](../vsto/caching-data.md)します。  
  
 キャッシュされたデータのビューを提供するには、Windows フォーム コントロールをバインドすることができますと*ホスト コントロール*データ アイランド内のオブジェクトをドキュメントにします。 データ アイランドと、データ バインド コントロールの間のデータ バインディングは、2 つの同期を維持します。 コントロールの独立したデータを検証コードを追加することもできます。 詳細については、次を参照してください。 [Office ソリューションでのコントロールにデータをバインド](../vsto/binding-data-to-controls-in-office-solutions.md)します。  
  
 ホスト コントロールは、バージョンの Excel および Word オブジェクト モデルでのネイティブ オブジェクトに拡張されます。 ネイティブのオブジェクトとは異なり、管理対象のデータ オブジェクトに直接ホスト コントロールをバインドできます。 詳細については、次を参照してください。[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)と[Windows フォーム コントロールの Office ドキュメントの概要](../vsto/windows-forms-controls-on-office-documents-overview.md)します。  
  
## <a name="access-cached-data-on-the-server"></a>アクセスは、サーバー上のデータをキャッシュします。  
 使用することができます、ドキュメント内のキャッシュされたデータにアクセスする、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>クラス。 このクラスの一部である、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]、し、実行中の Excel または Word なしのサーバーで使用できます。 ときに、ユーザーは、キャッシュされたデータを変更する、データにバインドされているすべてのコントロールは、変更を自動的に同期され、ユーザーには、更新されたデータが表示されます、ドキュメントを開きます。 詳細については、次を参照してください。[サーバー上のドキュメント内のデータ アクセス](../vsto/accessing-data-in-documents-on-the-server.md)します。  
  
 Excel および Word は、クライアントでの表示にのみ、サーバー上のデータに書き込むには必要ありません。 Excel および Word もする必要はありません、サーバーにインストールします。 これは、スケーラビリティの向上とデータ アイランドを含むドキュメントの高速のバッチ処理を実行する機能を提供します。  
  
## <a name="data-caching-for-offline-use"></a>データをオフラインで使用するキャッシュ  
 データ アイランドにデータを格納するオフラインのシナリオを実現できます。 ユーザーが最初にドキュメントを開くか、サーバーからドキュメントを要求、データ アイランドは、最新のデータを格納します。 データ アイランドは、ドキュメントにキャッシュされているしはオフライン利用できます。 ユーザー (とコード) は、ライブ接続が使用できない場合でも、データを操作することができます。 ユーザーが再接続するときは、サーバーのデータ ソースにデータへの変更を反映できます。  
  
## <a name="cached-data-and-custom-xml-parts-compared"></a>キャッシュされたデータとカスタム XML 部分の比較  
 カスタム XML 部分は、2007 Microsoft Office system のドキュメントの XML の任意の部分を格納する方法として導入されました。 カスタム XML 部分は多くのデータ キャッシュとして同じシナリオで便利ですが、いくつかの違いは、データ アイランドとカスタム XML 部分があります。 カスタム XML 部分の詳細については、次を参照してください。[カスタム XML 部分の概要](../vsto/custom-xml-parts-overview.md)します。  
  
 次の表では、相違点と共通の一部を示します。  
  
||データ キャッシュ|カスタム XML 部分|  
|-|----------------|----------------------|  
|Office アプリケーションには、これらを使用できますか。|次のアプリケーションのドキュメント レベルのカスタマイズ:<br /><br /> -Excel<br />ワード|次のアプリケーションのドキュメント レベルおよびアプリケーション レベルのソリューション:<br /><br /> -Excel<br />-PowerPoint<br />ワード|  
|どのような種類のデータを格納することができますか。|特定の要件を満たすカスタマイズ アセンブリ内の任意のパブリック オブジェクト。 詳細については、次を参照してください。[データ キャッシュ](../vsto/caching-data.md)します。|任意の XML データ。|  
|Microsoft Office アプリケーションを起動せず、データにアクセスすることができますか。|使用して、はい、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>クラスによって提供される、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]します。|内のクラスを使用して、[はい]、<xref:System.IO.Packaging>名前空間、または Open XML 形式の SDK を使用しています。|  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューションにおけるデータ](../vsto/data-in-office-solutions.md)   
 [Visual Studio での Office ソリューションのアーキテクチャ](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  