---
title: サーバー上のドキュメント内のデータへのアクセス
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], accessing on server
- data access [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b6203282404f6dc01f51f7cea68f90fa7a759c56
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="accessing-data-in-documents-on-the-server"></a>サーバー上のドキュメント内のデータへのアクセス
  Microsoft Office Word または Microsoft Office Excel のオブジェクト モデルを使用することがなく、ドキュメント レベルのカスタマイズ内のデータに対してプログラミングできます。 つまり、単語がないサーバー上のドキュメントに含まれているデータにアクセスすることができますか、Excel がインストールされていること。 たとえば、サーバー上のコード (などの[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] ページ)、ドキュメント内のデータをカスタマイズしてエンドユーザー向けにカスタマイズされた文書を送信します。 エンドユーザーが、ドキュメントを開いたときに、ソリューション アセンブリのデータ バインディング コードはカスタマイズされたデータをドキュメントにバインドします。 これには、ドキュメント内のデータは、ユーザー インターフェイスから分離されるためです。 詳細については、次を参照してください。[ドキュメント レベルのカスタマイズでキャッシュ データ](../vsto/cached-data-in-document-level-customizations.md)です。  

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  

## <a name="caching-data-for-use-on-a-server"></a>サーバーで使用するデータのキャッシュ  
 ドキュメント内のデータ オブジェクトをキャッシュするを使用してマークする、<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>デザイン時に、属性に使用するか、`StartCaching`実行時にホスト項目のメソッドです。 ドキュメント内のデータ オブジェクトをキャッシュすると、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]オブジェクトをドキュメントに格納されている XML 文字列にシリアル化します。 オブジェクトは、キャッシュの対象に特定の要件を満たす必要があります。 詳細については、「 [Caching Data](../vsto/caching-data.md)」を参照してください。  

 サーバー側コードでは、データ キャッシュ内の任意のデータ オブジェクトを操作できます。 キャッシュされたデータのインスタンスにバインドされているコントロールは、データに加えられたサーバー側の変更は、クライアントで、ドキュメントが開いているときに自動的に表示できるように、ユーザー インターフェイスと同期されます。  

## <a name="accessing-data-in-the-cache"></a>キャッシュ内のデータにアクセスします。  
 キャッシュ内のデータは、たとえば、コンソール アプリケーション、Windows フォーム アプリケーション、または Web ページから、オフィス外部からのアプリケーションからアクセスできます。 キャッシュされたデータにアクセスするアプリケーションは完全な信頼がある必要があります。部分的な信頼関係がある Web アプリケーションは、挿入、取得、または Office ドキュメントにキャッシュされているデータを変更することはできません。  

 データ キャッシュがによって公開されているコレクションの階層からアクセスできる、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>のプロパティ、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>クラス。  

-   <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>プロパティから返される、<xref:Microsoft.VisualStudio.Tools.Applications.CachedData>のすべてのドキュメント レベルのカスタマイズでキャッシュされたデータが含まれています。  

-   各<xref:Microsoft.VisualStudio.Tools.Applications.CachedData>1 つ以上含む<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>オブジェクト。 A<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>のすべての 1 つのクラス内で定義されているキャッシュされたデータ オブジェクトが含まれています。  

-   各<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>1 つ以上含む<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>オブジェクト。 A <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> 1 つのキャッシュされたデータ オブジェクトを表します。  

 次のコード例でキャッシュされた文字列にアクセスする方法を示します、 `Sheet1` Excel ブック プロジェクトのクラスです。 この例は提供されている長い例の一部である、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A>メソッドです。  

 [!code-csharp[Trin_ServerDocument#12](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#12)]
 [!code-vb[Trin_ServerDocument#12](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#12)]  

## <a name="modifying-data-in-the-cache"></a>キャッシュ内のデータを変更します。  
 キャッシュされたデータ オブジェクトを変更するには、通常次の手順を実行します。  

1.  オブジェクトの新しいインスタンスにキャッシュされたオブジェクトの XML 表現を逆シリアル化します。 使用して XML にアクセスすることができます、<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A>のプロパティ、<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>を表すキャッシュされたデータ オブジェクト。  

2.  このコピーに変更を加えます。  

3.  次のオプションのいずれかを使用して、データ キャッシュに変更されたオブジェクトをシリアル化します。  

    -   変更を自動的にシリアル化する場合を使用して、<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A>メソッドです。 このメソッドを使用して、 **DiffGram**のシリアル化形式<xref:System.Data.DataSet>、 <xref:System.Data.DataTable>、型指定されたデータ キャッシュ内のデータセット オブジェクト。 **DiffGram**形式、オフラインのドキュメント内のデータ キャッシュへの変更がサーバーに正しく送信されることを確認します。  

    -   キャッシュされたデータへの変更を独自のシリアル化を実行するかどうか、書き込めることに直接、<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A>プロパティです。 指定、 **DiffGram**形式を使用する場合、 <xref:System.Data.Common.DataAdapter> 、データベース内のデータに加えられた変更で更新する、 <xref:System.Data.DataSet>、 <xref:System.Data.DataTable>、またはデータセットの型を指定します。 それ以外の場合、<xref:System.Data.Common.DataAdapter>既存の行を変更する代わりに新しい行を追加することで、データベースを更新します。  

### <a name="modifying-data-without-deserializing-the-current-value"></a>現在の値を逆シリアル化せずにデータを変更します。  
 場合によっては、最初に現在の値を逆シリアル化せず、キャッシュされたオブジェクトの値を変更する可能性があります。 たとえば、行うことができますこの文字列や整数などの単純型を持つオブジェクトの値を変更する場合、またはキャッシュされた初期化する<xref:System.Data.DataSet>サーバー上のドキュメントでします。 このような場合は、使用することができます、<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A>最初に、キャッシュされたオブジェクトの現在の値を逆シリアル化せずメソッドです。  

 次のコード例は、キャッシュされた文字列内で値を変更する方法を示します、 `Sheet1` Excel ブック プロジェクトのクラスです。 この例は提供されている長い例の一部である、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A>メソッドです。  

 [!code-csharp[Trin_ServerDocument#11](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#11)]  

### <a name="modifying-null-values-in-the-data-cache"></a>データ キャッシュ内の Null 値を変更します。  
 データ キャッシュが値を持つオブジェクトを格納しない**null**ドキュメントを保存して閉じるとき。 このような制限では、キャッシュされたデータを変更するときにいくつかのような影響があります。  

-   値をデータ キャッシュ内で任意のオブジェクトを設定するかどうかは**null**、データ キャッシュ内のオブジェクトのすべてに自動的に設定されますが**null**とドキュメントが開き、ときに、全体のデータ キャッシュを消去は、ドキュメントを保存して終了します。 つまり、すべてのキャッシュされたオブジェクトが削除されますデータ キャッシュから、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>コレクションは空になります。  

-   ソリューションをビルドする場合**null**を使用してこれらのオブジェクトを初期化するため、データ キャッシュ内のオブジェクト、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>ドキュメントの前にクラスを初めて開くと、すべてのオブジェクトを初期化することを確認する必要がありますデータ キャッシュします。 一部のオブジェクトを初期化する場合のすべてのオブジェクトに設定されます**null**ドキュメントが開かれ、ドキュメントを保存して閉じるときに、全体のデータ キャッシュが消去します。  

## <a name="accessing-typed-datasets-in-the-cache"></a>キャッシュ内の型指定されたデータセットにアクセスします。  
 Office ソリューションと、オフィス外部から Windows フォーム アプリケーションなどのアプリケーションの両方に型指定されたデータセット内のデータにアクセスするかどうか、または[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]プロジェクト、両方で参照されている別のアセンブリに型指定されたデータセットを定義する必要がありますプロジェクト。 使用して、各プロジェクトに型指定されたデータセットを追加するかどうか、**データ ソース構成ウィザード**または**データセット デザイナー**、.NET Framework は異なる型として 2 つのプロジェクトで型指定されたデータセットを扱う. 型指定されたデータセットの作成の詳細については、次を参照してください。[作成して Visual Studio でのデータセットを構成する](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio)です。  

## <a name="see-also"></a>関連項目  
 [サーバー上のドキュメント内のデータにアクセスします。](../vsto/accessing-data-in-documents-on-the-server.md)   
 [ドキュメントレベルのカスタマイズのキャッシュ データ](../vsto/cached-data-in-document-level-customizations.md)  
