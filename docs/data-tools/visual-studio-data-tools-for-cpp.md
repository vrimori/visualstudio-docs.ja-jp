---
title: C++ 用のデータ ツール
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CPP
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
- cplusplus
ms.openlocfilehash: 4c247d693da287581b8ab163880e9cecf4aeb17c
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304926"
---
# <a name="visual-studio-data-tools-for-c"></a>C++ 用の Visual Studio データ ツール

多くの場合、ネイティブ C++ は、データ ソースにアクセスするときに、最速のパフォーマンスを提供します。 ただし、ツールの Visual Studio での C++ アプリケーションのデータは、.NET アプリケーションはそれほど高度ではありません。 たとえば、**データソース**にドラッグ アンド ドロップを C++ のデザイン画面にデータ ソース ウィンドウを使用することはできません。 オブジェクト リレーショナル レイヤーを必要な場合は独自に作成またはサード パーティ製の製品を使用する必要があります。 Microsoft Foundation Class ライブラリを使用するアプリケーションはメモリにデータを格納し、ユーザーに表示するドキュメントとビュー、と共に、いくつかのデータベース クラスを使用することもできますも、データ バインディング機能についても同様です。 詳細については、次を参照してください。 [Visual c でのデータ アクセス](/cpp/data/data-access-in-cpp)します。

SQL データベースに接続するには、ネイティブ C++ アプリケーションは、ODBC および OLE DB ドライバーおよび ADO プロバイダーは、Windows に含まれているを使用できます。 これらは、それらのインターフェイスをサポートする任意のデータベースに接続できます。 ODBC ドライバーは、標準です。 OLE DB は、旧バージョンとの互換性のために提供されます。 このようなデータ テクノロジの詳細については、次を参照してください。 [Windows Data Access Components](/previous-versions/windows/desktop/ms692897(v=vs.85))します。

SQL Server 2005 でのカスタム機能を利用し、後で、使用して、 [SQL Server native client](/sql/relational-databases/native-client/sql-server-native-client)します。 ネイティブ クライアントでは、SQL Server ODBC ドライバーと 1 つのネイティブ ダイナミック リンク ライブラリ (DLL) で SQL Server OLE DB プロバイダーも含まれています。 これらは、Microsoft SQL Server にネイティブ コード Api (ODBC、OLE DB と ADO) を使用してアプリケーションをサポートします。 SQL Server Native Client は、SQL Server Data Tools と共にインストールされます。 プログラミング ガイドはこちら: [SQL Server native client プログラミング](/sql/relational-databases/native-client/sql-server-native-client-programming)します。

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>C++ アプリケーションから ODBC および SQL Native Client で localDB に接続するには

1. SQL Server Data Tools のインストール

2. サンプル SQL データベースに接続する場合は、Northwind データベースをダウンロードし、新しい場所に解凍します。

3. SQL Server Management Studio を使用して、アタッチ、解凍*Northwind.mdf* localDB へのファイル。 SQL Server Management Studio の起動時には、「(localdb) \MSSQLLocalDB に接続します。

   ![SSMS 接続ダイアログ](../data-tools/media/raddata-ssms-connect-dialog.png)

   左側のウィンドウで [localdb] ノードを右クリックしを選択し、**アタッチ**します。

   ![SSMS でデータベースをアタッチします。](../data-tools/media/raddata-ssms-attach-database.png)

4. ODBC の Windows SDK サンプルをダウンロードして、新しい場所に解凍します。 このサンプルでは、データベースと問題のクエリとコマンドへの接続に使用される ODBC の基本的なコマンドを示します。 これらの関数に関する詳細については、 [Microsoft Open Database Connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc)します。 最初に読み込む (C++ フォルダーには) ソリューション、ソリューションを Visual Studio の現在のバージョンにアップグレードする Visual Studio が提供されます。 **[はい]** をクリックします。

5. ネイティブ クライアントを使用する必要がその*ヘッダー*ファイルと*lib*ファイル。 これらのファイルには、関数および sql.h で定義された ODBC 関数以外の SQL Server に固有の定義が含まれます。 **プロジェクト** > **プロパティ** > **vc++ ディレクトリ**次のインクルード ディレクトリを追加します。

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Include**

   このライブラリ ディレクトリ:

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Lib**

6. これらの行を追加*odbcsql.cpp*します。 #Define コンパイルされない無関係な OLE DB 定義を防止します。

   ```cpp
   #define _SQLNCLI_ODBC_
   #include <sqlncli.h>
   ```

    そのサンプルで実際に使用されない、ネイティブ クライアントの機能のため、上記の手順はコンパイルして実行する必要はありませんに注意してください。 ただし、この機能を使用するため、プロジェクトが構成されているようになりました。 詳細については、「[SQL Server Native Client プログラミング](/sql/relational-databases/native-client/sql-server-native-client)」を参照してください。

7. ODBC サブシステムで使用するドライバーを指定します。 サンプルでは、コマンドライン引数としてのドライバー接続文字列の属性を渡します。 **プロジェクト** > **プロパティ** > **デバッグ**、このコマンドの引数を追加します。

   ```cpp
   DRIVER="SQL Server Native Client 11.0"
   ```

8. **F5** キーを押してアプリケーションをビルドし、実行します。 データベースを入力するように求められますドライバーからのダイアログ ボックスを表示する必要があります。 入力`(localdb)\MSSQLLocalDB`、確認と**セキュリティ接続を使用**します。 [OK] を押します。 接続に成功を示すメッセージをコンソールに表示されます。 表示されます、コマンド プロンプトで SQL ステートメントを入力することができます。 次の画面には、クエリの例と、結果が表示されます。

   ![ODBC のサンプル クエリの出力](../data-tools/media/raddata-odbc-sample-query-output.png)

## <a name="see-also"></a>関連項目

- [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)