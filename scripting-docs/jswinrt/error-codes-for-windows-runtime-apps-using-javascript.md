---
title: "JavaScript を使用した Windows ランタイム アプリのエラー コード | Microsoft Docs"
ms.custom: 
ms.date: 05/10/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- JavaScript, Windows Runtime error codes
- VS.WebClient.Help.APPHOST9601
- VS.WebClient.Help.APPHOST9602
- VS.WebClient.Help.APPHOST9603
- VS.WebClient.Help.APPHOST9604
- VS.WebClient.Help.APPHOST9605
- VS.WebClient.Help.APPHOST9606
- VS.WebClient.Help.APPHOST9607
- VS.WebClient.Help.APPHOST9608
- VS.WebClient.Help.APPHOST9610
- VS.WebClient.Help.APPHOST9611
- VS.WebClient.Help.APPHOST9613
- VS.WebClient.Help.APPHOST9614
- VS.WebClient.Help.APPHOST9615
- VS.WebClient.Help.APPHOST9616
- VS.WebClient.Help.APPHOST9617
- VS.WebClient.Help.APPHOST9618
- VS.WebClient.Help.APPHOST9619
- VS.WebClient.Help.APPHOST9620
- VS.WebClient.Help.APPHOST9623
- VS.WebClient.Help.APPHOST9624
- VS.WebClient.Help.APPHOST9626
ms.assetid: 4c6d4e90-602a-4b56-ae74-3458929da442
caps.latest.revision: 1
author: erikadoyle
ms.author: edoyle
manager: jken
ms.translationtype: HT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 89b91a3246d0a6e2980459c2c35c7361168bccd4
ms.contentlocale: ja-jp
ms.lasthandoff: 08/11/2017

---
# <a name="error-codes-for-windows-runtime-apps-using-javascript"></a>JavaScript を使用した Windows ランタイム アプリのエラー コード
ここでは、JavaScript を使用した Windows ランタイム アプリの開発時に Microsoft Visual Studio コンソールに表示されるエラー コードを示します。
  
エラー | コメント
----- | -------
APPHOST9601: "*remoteURI* を読み込むことができません。 アプリでは、ローカル コンテキストにリモート Web コンテンツを読み込むことはできません。" | Web コンテキストで許可されている内容の詳細については、「[各コンテキストの機能と制限 (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx)」を参照してください。
APPHOST9602: "'javascript:' は無効な属性値であるため、無視されます。 ローカル コンテキストでは、'javascript:' URI を使用しないでください。" | セキュリティ上の理由から、ローカル コンテキストでは 'javascript:' URI を使用することはできません。 ローカル コンテキストで許可されている内容の詳細については、「[各コンテキストの機能と制限 (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx)」を参照してください。
APPHOST9603: "クラス ID が '*classID*' の ActiveX プラグインを読み込むことはできません。  アプリは、ActiveX コントロールを読み込めません。" | JavaScript を使用する Windows ランタイム アプリでは、カスタムの Microsoft ActiveX コントロールはサポートされていません。 UI コントロールが必要な場合は、標準 Web コントロール、コントロール ライブラリを使用するか、独自のカスタム コントロールを作成します。 カスタム ロジックを実行する必要がある場合は、代わりにカスタムの Windows ランタイム オブジェクトを作成します。 その他の HTML、CSS、および JavaScript の違いについては、「[HTML、CSS、JavaScript の機能と違い (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465380.aspx)」を参照してください。
APPHOST9604: "無効な文字エンコードが使用されているため、*uri* に移動できません。  アプリでは、UTF8 でエンコードされたファイルにしか移動できません。" | Windows ランタイムによってアクセスされるすべての HTML、JavaScript、および CSS は、8 ビットの Unicode Transformation Format (UTF-8) としてエンコードする必要があります。 その他の HTML、CSS、および JavaScript の違いについては、「[HTML、CSS、JavaScript の機能と違い (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465380.aspx)」を参照してください。
APPHOST9605: "移動先 URI がより高レベルのセキュリティ ゾーンにあるため、*sourceURI* から *targetURI* に移動できません。 セキュリティのレベルが低いゾーンから高いゾーンに移動できるのは、Web コンテキストの URI からローカル コンテキストの URI に移動する場合で、ローカル コンテキストの URI が MSApp.addPublicLocalApplicationUri メソッドに登録されている場合に限られます。" | 詳細については、「[MSApp.addPublicLocalApplicationUri](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465759.aspx)」を参照してください。
APPHOST9606: "HTTP 接続を使用していますが、ms-https-connections-only メタ要素が存在するため、*uri* を読み込むことができません。 ms-https-connections-only メタ要素を使用する場合は、HTTPS 接続しか使用できません。 HTTPS 接続を使用するか、セキュリティで保護された接続が不要な場合はメタ要素を削除してください。" | 詳細については、「[HTTPS 接続の要求方法 (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh452771.aspx)」を参照してください。
APPHOST9607: "次のエラーのため、アプリは URI (*uri*) を起動できません: *failureCode*。" | リソースの欠落または無効なファイルがこのエラーの一般的な原因です。
APPHOST9608: "次のエラーのため、アプリは about:blank ページに移動できませんでした: *errorCode*。" | 
APPHOST9610: "カスタム エラー ページへの移動の準備中に、アプリでエラーが見つかりました: *errorCode*。" |
APPHOST9611: "次のエラーのため、アプリはカスタム エラー ページに移動できませんでした: *errorCode*。" |
APPHOST9613: "次のエラーのため、アプリは * uri* に移動できませんでした: *errorCode*。" | 
APPHOST9614: "iFrame 内のドキュメントが *requestedDocMode* ドキュメント モードを要求しましたが、システムによって *currentDocMode* ドキュメント モードが強制されています。 iframe では *currentDocMode* ドキュメント モードが使用されます。" | リモート Web コンテンツの表示の詳細については、「[外部の Web ページにリンクする方法 (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh780594.aspx)」を参照してください。
APPHOST9615: "*uri* のファイルはローカル コンテキストの外部でプログラムによって呼び出されたため、アプリはこのファイルをダウンロードできません。" | Web コンテキストのコンテンツがプログラムでファイルをダウンロードしようとするときに発生します。
APPHOST9616: "この URI は地理位置情報 API を使用できません。  地理位置情報 API は、パッケージの一部である URI か、マニフェストの ApplicationContentUris 要素に含まれている URI からのみ呼び出すことができます。" | Web コンテキストで許可されている内容の詳細については、「[各コンテキストの機能と制限 (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx)」を参照してください。
APPHOST9617: "この URI はクリップボード API を使用できません。  クリップボード API は、パッケージの一部である URI か、マニフェストの ApplicationContentUris 要素に含まれている URI からのみ呼び出すことができます。" | Web コンテキストで許可されている内容の詳細については、「[各コンテキストの機能と制限 (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx)」を参照してください。
APPHOST9618: "この URI は window.close を使用できません。  window.close メソッドは、ms-appx URI スキームを使用して読み込まれたパッケージ コンテンツからのみ呼び出すことができます。" | Web コンテキストで許可されている内容の詳細については、「[各コンテキストの機能と制限 (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx)」を参照してください。
APPHOST9619: "Web コンテキスト内のページはアプリのトップ レベル ドキュメントにできないため、アプリは *uri* に移動できません。 代わりに、ページを iframe に読み込んでください。" | リモート Web ページには最上位レベルのページを移動できませんが、アプリは [iframe](https://msdn.microsoft.com/en-us/library/ms535258(v=vs.85).aspx) で Web ページを表示することができます。 リモート Web コンテンツの表示の詳細については、「[外部の Web ページにリンクする方法 (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh780594.aspx)」を参照してください。
APPHOST9620: "このアプリは HTTP 接続を使用しましたが、ms-https-connections-only メタ要素が存在するため、アプリは閉じられました。 ms-https-connections-only メタ要素を使用する場合は、HTTPS 接続しか使用できません。 HTTPS 接続を使用するか、セキュリティで保護された接続が不要な場合はメタ要素を削除してください。" | 詳細については、「[HTTPS 接続の要求方法 (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh452771.aspx)」を参照してください。
APPHOST9623: "次のエラーのため、アプリは *url* を解決できませんでした: *errorCode*。" | このエラーの一般的な原因はファイルの欠落です。  
APPHOST9624: "アプリはスクリプトを使用して *url* URL を読み込めません。この URL は別のアプリを起動するためです。 別のアプリを起動できるのは、ユーザーが直接操作した場合だけです。" | アプリは他のアプリを直接起動できません。 アプリが特定のコントラクトを実装する場合は、ユーザーが他のアプリを起動できます。 詳細については、「[アプリ コントラクトと拡張機能 (Windows ランタイム アプリ)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh464906.aspx)」を参照してください。
APPHOST9626: "リソース ファイル `ms-appx://1d33240b-0b00-40e4-a416-a4750c48787f/ja-jp\images\logo.scale-140.png` への直接参照が検出されました。 この参照は、デバッグ環境の外部で使用されるとエラーになります。" | `logo.scale-140.png` のファイル パスにより、この PNG ファイルはローカライズされたリソースとして扱われるため、ローカライズされたリソースを直接参照できないというエラーが発生します。 このファイルを言語リソースとして使用する場合は、「[アプリのグローバル化 (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465006.aspx)」を参照してください。 それ以外の場合は、問題のあるディレクトリの名前を変更してみてください。
  
## <a name="see-also"></a>関連項目  
 [JavaScript での Windows ランタイムの使用](../jswinrt/using-the-windows-runtime-in-javascript.md)
