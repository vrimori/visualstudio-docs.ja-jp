---
title: '方法: 接続文字列を保存および編集する'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 050d5f7bcda86890642a5bef10fa04d2c12b4203
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089232"
---
# <a name="how-to-save-and-edit-connection-strings"></a>方法: を保存し、接続文字列の編集
Visual Studio アプリケーションで接続文字列は (アプリケーション設定とも呼ばれます)、アプリケーション構成ファイルに保存または、アプリケーションに直接ハードコーディングします。 接続文字列をアプリケーション構成ファイルに保存すると、アプリケーションの保守タスクが簡単になります。 接続文字列を変更する必要がある場合は、(ソース コードで変更して、アプリケーションを再コンパイルすること) ではなく、アプリケーション設定ファイルで更新できます。

接続文字列内に機密情報 (パスワードなど) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。 アプリケーション構成ファイルに保存された接続文字列は暗号化も難読化もされないため、第三者がファイルにアクセスしてコンテンツを表示する可能性があります。 データベースへのアクセスを制御する方法としては、Windows 統合セキュリティを使用する方が安全です。

Windows 統合セキュリティを使用しない環境で、データベースにユーザー名とパスワードが必要な場合、接続文字列からユーザー名とパスワードを削除できます。ただし、データベースに正常に接続するには、この情報をアプリケーションから提供する必要があります。 たとえば、ユーザーにこの情報を要求するダイアログ ボックスを作成し、実行時に接続文字列を動的にビルドできます。 この方法でも、情報がデータベースに送信される途中で傍受された場合は、セキュリティの問題が発生する可能性があります。
詳細については、次を参照してください。[接続情報の保護](/dotnet/framework/data/adonet/protecting-connection-information)します。

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>データ ソース構成ウィザード内から接続文字列を保存するには
**データ ソース構成ウィザード**で、接続を保存するオプションを選択、**アプリケーション構成ファイルへの接続文字列を保存**ページ。

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>接続文字列をアプリケーション設定に直接保存するには
1. **ソリューション エクスプ ローラー**、ダブルクリックして、 **My Project**アイコン (Visual Basic) または**プロパティ**アイコン (c#) を開く、**プロジェクト デザイナー**.
1. 選択、**設定**タブ。
1. 入力、**名前**の接続文字列。 コードで接続文字列にアクセスするときにこの名前を参照します。
1. 設定、**型**に (**接続文字列**)。
1. ままに、**スコープ**設定**アプリケーション**します。
1. 接続文字列を入力、**値**フィールド、またはをクリックして、**省略記号**(...) ボタン、**値**フィールドを開く、 **接続のプロパティ**  ダイアログ ボックス、接続文字列を作成します。

## <a name="edit-connection-strings-stored-in-application-settings"></a>アプリケーションの設定に格納されている接続文字列を編集します。
使用してアプリケーションの設定に保存されている接続情報を変更することができます、**プロジェクト デザイナー**します。

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>アプリケーション設定に格納された接続文字列を編集するには
1. **ソリューション エクスプ ローラー**、ダブルクリックして、 **My Project**アイコン (Visual Basic) または**プロパティ**アイコン (c#) を開く、**プロジェクト デザイナー**.
1. 選択、**設定**タブ。
1. 編集し、テキストを選択し接続が見つかりません、**値**フィールド。
1. 内の接続文字列を編集、**値**フィールド、またはをクリックして、**省略記号**(...) ボタン、**値**との接続を編集するフィールド、**接続プロパティ** ダイアログ ボックス。

## <a name="edit-connection-strings-for-datasets"></a>データセットの接続文字列を編集します。
データセット内の各 TableAdapter の接続情報を変更することができます。

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>TableAdapter がデータセット内の接続文字列を編集するには
1. **ソリューション エクスプ ローラー**、データセットをダブルクリックします (**.xsd**ファイル) を編集する接続を持ちます。
1. 選択、 **TableAdapter**またはクエリを編集する接続があります。
1. **プロパティ**ウィンドウで、展開、**接続ノード**します。
1. 接続文字列をすばやく変更するには、編集、 **ConnectionString**プロパティ、下矢印をクリックしてまたは、**接続**プロパティ選択**新しい接続**します。

## <a name="security"></a>セキュリティ
接続文字列内に機密情報 (パスワードなど) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。 データベースへのアクセスを制御する方法としては、Windows 統合セキュリティを使用する方が安全です。
詳細については、次を参照してください。[接続情報の保護](/dotnet/framework/data/adonet/protecting-connection-information)します。

## <a name="see-also"></a>関連項目

- [接続の追加](../data-tools/add-new-connections.md)