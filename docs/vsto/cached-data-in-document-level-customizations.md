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
ms.openlocfilehash: bd93d985b72f945e7a1c70199d6ff3aacf5f0229
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="cached-data-in-document-level-customizations"></a>ドキュメント レベルのカスタマイズでキャッシュされたデータ
  ドキュメント レベルのカスタマイズの主な目的では、Office ドキュメントのビューからデータを分離します。 データは、数値やテキストなど、ドキュメントに格納されている情報を参照します。 ビューは、ユーザー インターフェイスおよび Microsoft Office Word および Microsoft Office Excel のオブジェクト モデルを指します。  
  
 Visual Studio では、ドキュメント レベルのカスタマイズのビューからデータを分離として埋め込まれるデータを有効にすると、*データ アイランド*もという、*データ キャッシュ*です。 読み取りまたは Word または Excel を起動せずに直接データを変更できます。 これは、Microsoft Office がインストールされていないサーバー上のドキュメント内のデータを変更する必要がある場合に便利です。 クライアント環境で使用するためのものでは、Word および Excelサーバー上で実行する、設計されていません。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 ドキュメント レベルのカスタマイズの詳細については、次を参照してください。 [Office ソリューション開発の概要&#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md)と[ドキュメント レベルのカスタマイズのアーキテクチャ](../vsto/architecture-of-document-level-customizations.md)です。  
  
## <a name="understand-the-cached-data-programming-model"></a>キャッシュされたデータのプログラミング モデルについての理解します。  
 データ アイランドは、特定の要件を満たすソリューション内の任意のオブジェクトを含めることができます。 これらのオブジェクトを含める<xref:System.Data.DataSet>オブジェクト、<xref:System.Data.DataTable>オブジェクト、およびその他のオブジェクトをシリアル化可能な<xref:System.Xml.Serialization.XmlSerializer>クラスです。 詳細については、次を参照してください。 を参照してください[データ キャッシュ](../vsto/caching-data.md)です。  
  
 キャッシュされたデータのビューを提供するには、Windows フォーム コントロールをバインドすることができ、*ホスト コントロール*データ アイランド内のオブジェクトをドキュメントにします。 データ アイランドと、データ バインド コントロール間のデータ バインディングは、同期を保持します。 別のコントロールのデータに検証コードを追加することもできます。 詳細については、次を参照してください。 [Office ソリューションでのコントロールにデータをバインド](../vsto/binding-data-to-controls-in-office-solutions.md)です。  
  
 ホスト コントロールは、バージョンの Excel および Word オブジェクト モデルでのネイティブ オブジェクトに拡張されています。 ネイティブのオブジェクトとは異なり、マネージ データ オブジェクトに直接ホスト コントロールをバインドできます。 詳細については、次を参照してください。[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)と[Office ドキュメントの概要 Windows フォームのコントロール](../vsto/windows-forms-controls-on-office-documents-overview.md)です。  
  
## <a name="access-cached-data-on-the-server"></a>アクセスは、サーバー上のデータをキャッシュします。  
 ドキュメントでキャッシュされたデータにアクセスする際、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>クラスです。 このクラスの一部である、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]、実行中の Excel または Word をサーバーで使用できます。 ときに、ユーザーでは、キャッシュされたデータを変更する、データにバインドされている任意のコントロールは、変更に自動的に同期して、ユーザーが更新されたデータの表示が後にドキュメントが開きます。 詳細については、次を参照してください。[サーバー上のドキュメント内のデータ アクセス](../vsto/accessing-data-in-documents-on-the-server.md)です。  
  
 Excel および Word は、クライアントでの表示にのみ、サーバー上にデータを書き込む必要がないです。 Excel および Word 必要もありませんサーバーにインストールします。 これは、スケーラビリティの向上やデータ アイランドを含むドキュメントの高速のバッチ処理を実行する機能を提供します。  
  
## <a name="data-caching-for-offline-use"></a>オフラインで使用できるキャッシュ データ  
 データ アイランドにデータを格納するオフラインのシナリオを実現できます。 ユーザーが初めてドキュメントを開くとしたり、サーバーからドキュメントを要求、ときに、データ アイランドは、最新のデータが入力されます。 データ アイランドは、ドキュメント内にキャッシュし、は、オフラインで使用します。 ユーザー (およびコード) は、ライブ接続が使用できない場合でもデータを操作することができます。 ユーザーが再接続された場合は、サーバーのデータ ソースにデータへの変更を反映できます。  
  
## <a name="cached-data-and-custom-xml-parts-compared"></a>キャッシュされたデータとカスタム XML 部分の比較  
 カスタム XML 部分は、ドキュメント内の XML の任意の部分を格納する方法として、2007 Microsoft Office system で導入されました。 カスタム XML 部分は、データ キャッシュとして同じシナリオの多くで役に立ちますが、いくつかの違いは、データ アイランドとカスタム XML 部分があります。 カスタム XML 部分の詳細については、次を参照してください。[カスタム XML 部分の概要](../vsto/custom-xml-parts-overview.md)です。  
  
 次の表では、いくつか相違点と共通の一覧表示します。  
  
||データ キャッシュ|カスタム XML 部分|  
|-|----------------|----------------------|  
|Office アプリケーションは、これらを使用できますか。|次のアプリケーション用ドキュメント レベルのカスタマイズ:<br /><br /> -Excel<br />ワード|次のアプリケーション用のドキュメント レベルとアプリケーション レベルのソリューション:<br /><br /> -Excel<br />-PowerPoint<br />ワード|  
|どのような種類のデータを格納することができますか。|特定の要件を満たしているカスタマイズ アセンブリ内の任意のパブリック オブジェクト。 詳細については、次を参照してください。[データ キャッシュ](../vsto/caching-data.md)です。|任意の XML データです。|  
|Microsoft Office アプリケーションを起動せず、データにアクセスすることができますか。|使用して、はい、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>によって提供されるクラス、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]です。|クラスを使用して、はい、<xref:System.IO.Packaging>名前空間、または Open XML 形式の SDK を使用しています。|  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューションにおけるデータ](../vsto/data-in-office-solutions.md)   
 [Visual Studio での Office ソリューションのアーキテクチャ](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  