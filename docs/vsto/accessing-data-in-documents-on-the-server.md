---
title: サーバー上のドキュメントのデータにアクセス
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
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 70c00a9c0de4afd9f54062e1c2ffabcc2911a538
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305573"
---
# <a name="access-data-in-documents-on-the-server"></a>サーバー上のドキュメントのデータにアクセス
  Microsoft Office Word または Microsoft Office Excel のオブジェクト モデルを使用することがなく、ドキュメント レベル カスタマイズ内のデータに対してプログラミングできます。 つまり、Excel がインストールされてまたは Word がないサーバー上のドキュメントに含まれているデータにアクセスすることができます。 サーバーのコード例については、(たとえば、[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]ページ)、ドキュメント内のデータをカスタマイズおよびカスタマイズされたドキュメントをエンドユーザーに送信できます。 エンド ユーザーでは、文書が開いたら、ソリューション アセンブリにデータ バインド コードは、ドキュメントにカスタマイズされたデータをバインドします。 ユーザー インターフェイスから、ドキュメント内のデータが区切られたため、可能です。 詳細については、次を参照してください。[ドキュメント レベルのカスタマイズでキャッシュされたデータ](../vsto/cached-data-in-document-level-customizations.md)します。  

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  

## <a name="cache-data-for-use-on-a-server"></a>サーバーで使用するためのデータをキャッシュします。  
 ドキュメント内のデータ オブジェクトをキャッシュするでをマーク、 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 、デザイン時に属性またはを使用して、`StartCaching`メソッドの実行時にホスト項目。 ドキュメント内のデータ オブジェクトをキャッシュするときに、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]ドキュメントに格納されている XML 文字列にオブジェクトをシリアル化します。 オブジェクトは、キャッシュの対象にする特定の要件を満たす必要があります。 詳細については、次を参照してください。[データ キャッシュ](../vsto/caching-data.md)します。  

 サーバー側コードでは、データ キャッシュ内の任意のデータ オブジェクトを操作できます。 キャッシュされたデータのインスタンスにバインドされているコントロールは、データに行われたサーバー側の変更は、クライアントのドキュメントを開いたときに自動的に表示されるように、ユーザー インターフェイスと同期されます。  

## <a name="access-data-in-the-cache"></a>キャッシュのデータにアクセス  
 キャッシュ内のデータは、たとえば、コンソール アプリケーション、Windows フォーム アプリケーション、または Web ページから、オフィス外部からのアプリケーションからアクセスできます。 キャッシュされたデータにアクセスするアプリケーションでは完全な信頼が必要部分的な信頼関係がある Web アプリケーションは、挿入、取得、または Office ドキュメントにキャッシュされているデータを変更することはできません。  

 データ キャッシュがによって公開されているコレクションの階層からアクセスできる、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>のプロパティ、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>クラス。  

- <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>プロパティを返します、 <xref:Microsoft.VisualStudio.Tools.Applications.CachedData>、すべてのドキュメント レベル カスタマイズでキャッシュされたデータが含まれています。  

- 各<xref:Microsoft.VisualStudio.Tools.Applications.CachedData>1 つ以上含む<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>オブジェクト。 A <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> 1 つのクラス内で定義されているキャッシュされたデータ オブジェクトのすべてが含まれます。  

- 各<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>1 つ以上含む<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>オブジェクト。 A <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> 1 つのキャッシュされたデータ オブジェクトを表します。  

  次のコード例でキャッシュされた文字列にアクセスする方法を示します、 `Sheet1` Excel ブック プロジェクトのクラス。 この例のために用意されている長い例は、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A>メソッド。  

  [!code-csharp[Trin_ServerDocument#12](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#12)]
  [!code-vb[Trin_ServerDocument#12](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#12)]  

## <a name="modify-data-in-the-cache"></a>キャッシュ内のデータを変更します。  
 キャッシュされたデータ オブジェクトを変更するには、通常は次の手順を実行します。  

1.  オブジェクトの新しいインスタンスに、キャッシュされたオブジェクトの XML 表現を逆シリアル化します。 使用して XML にアクセスすることができます、<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A>のプロパティ、<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>を表すキャッシュされたデータ オブジェクト。  

2.  このコピーに変更を行います。  

3.  次のオプションのいずれかを使用して、データ キャッシュに再度変更されたオブジェクトをシリアル化します。  

    -   変更を自動的にシリアル化する場合を使用して、<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A>メソッド。 このメソッドを使用して、 **DiffGram**のシリアル化形式<xref:System.Data.DataSet>、 <xref:System.Data.DataTable>、型指定されたデータ キャッシュ内のデータセット オブジェクトとします。 **DiffGram**形式により、オフライン ドキュメント内のデータ キャッシュへの変更がサーバーに正しく送信されるようになります。  

    -   キャッシュされたデータに対する変更の独自のシリアル化を実行するかどうか、書き込めるに直接、<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A>プロパティ。 指定、 **DiffGram**形式を使用する場合、<xref:System.Data.Common.DataAdapter>内のデータに加えられた変更とデータベースを更新する、 <xref:System.Data.DataSet>、 <xref:System.Data.DataTable>、またはデータセットの型します。 それ以外の場合、<xref:System.Data.Common.DataAdapter>既存の行を変更する代わりに新しい行を追加することで、データベースを更新します。  

### <a name="modify-data-without-deserializing-the-current-value"></a>現在の値を逆シリアル化せずにデータを変更します。  
 場合によっては、最初に現在の値を逆シリアル化せず、キャッシュされたオブジェクトの値を変更する可能性があります。 たとえば、これを行う文字列や整数などの単純な型を持つオブジェクトの値を変更する場合、またはキャッシュされた初期化する<xref:System.Data.DataSet>サーバー上のドキュメントにします。 このような場合は、使用することができます、<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A>メソッドを最初に、キャッシュされたオブジェクトの現在の値を逆シリアル化なし。  

 次のコード例は、キャッシュされた文字列内で値を変更する方法を示します、 `Sheet1` Excel ブック プロジェクトのクラス。 この例のために用意されている長い例は、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A>メソッド。  

 [!code-csharp[Trin_ServerDocument#11](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#11)]  

### <a name="modify-null-values-in-the-data-cache"></a>データ キャッシュ内の null 値を変更します。  
 データ キャッシュは、値を持つオブジェクトを格納していない**null**ドキュメントを保存して閉じる。 この制限はキャッシュされたデータを変更するときに複数の結果があります。  

-   値にデータ キャッシュ内の任意のオブジェクトを設定するかどうか**null**、すべてのデータ キャッシュ内のオブジェクトに自動的に設定するが**null**とドキュメントが開かれ、ときに、すべてのデータ キャッシュをクリアするが、ドキュメントを保存して終了します。 データ キャッシュから、そのは、すべてのキャッシュされたオブジェクトの削除は、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>コレクションは空になります。  

-   ソリューションをビルドする場合**null**を使用してこれらのオブジェクトを初期化するために必要なデータ キャッシュ内のオブジェクト、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>ドキュメントの前にクラスを初めて開くと、すべてのオブジェクトを初期化することを確認する必要がありますデータ キャッシュします。 一部のオブジェクトを初期化すると、このすべてのオブジェクトを設定する**null**ドキュメントが開かれ、ドキュメントを保存して閉じられたときに、すべてのデータ キャッシュがクリアします。  

## <a name="access-typed-datasets-in-the-cache"></a>アクセス、キャッシュに型指定されたデータセット  
 Office ソリューションと、Windows フォーム アプリケーションなどのオフィス外部からアプリケーションの両方に型指定されたデータセット内のデータをアクセスするかどうか、または[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]プロジェクトでは、両方で参照されている別のアセンブリに型指定されたデータセットを定義する必要がありますプロジェクト。 使用して、各プロジェクトに型指定されたデータセットを追加するかどうか、**データ ソースの構成**ウィザードまたは**データセット デザイナー**、.NET Framework はさまざまな種類として 2 つのプロジェクトで型指定されたデータセットを扱う. 型指定されたデータセットを作成する方法の詳細については、次を参照してください。[作成し、Visual Studio でのデータセットを構成](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio)します。  

## <a name="see-also"></a>関連項目  
 [サーバー上のドキュメントのデータにアクセス](../vsto/accessing-data-in-documents-on-the-server.md)   
 [ドキュメント レベルのカスタマイズでキャッシュされたデータ](../vsto/cached-data-in-document-level-customizations.md)  
