---
title: 'チュートリアル: JavaScript を使用して、SDK の作成 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2132269329c8b6af3ac846596adea7b3462db5bf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-an-sdk-using-javascript"></a>チュートリアル: JavaScript を使用して SDK を作成します。
このチュートリアルでは、JavaScript を使用して単純な数学 SDK と Visual Studio Extension (VSIX) を作成する方法を説明します。  このチュートリアルは、これらのパートに分かれています。  
  
-   [SimpleMathVSIX 拡張機能 SDK プロジェクトを作成するには](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)  
  
-   [SDK を使用するサンプル アプリを作成するには](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)  
  
 [JavaScript]、クラス ライブラリ プロジェクトの種類はありません。 このチュートリアルでは、VSIX プロジェクトに直接サンプル arithmetic.js ファイルが作成されます。 実際には、最初にビルドおよびテストすること、JavaScript および CSS ファイル、Windows ストア アプリとしてことをお勧め — たとえばを使用して、**空のアプリケーション**テンプレート: VSIX プロジェクトに配置する前にします。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルに従うには、Visual Studio SDK をインストールする必要があります。 詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)です。  
  
##  <a name="createSimpleMathVSIX"></a> SimpleMathVSIX 拡張機能 SDK プロジェクトを作成するには  
  
1.  メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]**の順にクリックします。  
  
2.  テンプレート カテゴリの一覧で  **Visual c#****機能拡張**、し、、 **VSIX プロジェクト**テンプレート。  
  
3.  **名**テキスト ボックスで、指定`SimpleMathVSIX`を選択し、 **OK**ボタンをクリックします。  
  
4.  場合、 **Visual Studio パッケージ ウィザード**が表示されたら、選択、 **次へ**ボタンをクリックして、**へようこそ**  ページで、し**7 の 1 ページ目**を選択して、**完了**ボタンをクリックします。  
  
     ただし、**マニフェスト デザイナー**が開き、スクリプトを紹介するこのチュートリアル単純なマニフェスト ファイルを直接変更することによりします。  
  
5.  **ソリューション エクスプ ローラー**source.extension.vsixmanifest ファイルのショートカット メニューを開きを選択し、**コードの表示**です。 このコードを使用して、ファイルの既存のコンテンツを置き換えます。  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">  
      <Metadata>  
        <Identity Id="SimpleMathVSIX" Version="1.0" Language="en-US" Publisher="myname" />  
        <DisplayName>Simple Math</DisplayName>  
        <Description>Does basic arithmetic calculations.</Description>  
      </Metadata>  
      <Installation Scope="Global" AllUsers="true">  
        <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" />  
      </Installation>  
      <Dependencies>  
        <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" />  
      </Dependencies>  
      <Assets>  
        <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />  
      </Assets>  
    </PackageManifest>  
    ```  
  
6.  **ソリューション エクスプ ローラー**SimpleMathVSIX プロジェクトのショートカット メニューを開きを選択し、**追加**、**新しい項目の**します。  
  
7.  **データ**カテゴリで、 **XML ファイル**、ファイルの名前を付けます`SDKManifest.xml`を選択し、**追加**ボタンをクリックします。  
  
8.  **ソリューション エクスプ ローラー**sdkmanifest.xml 内ファイルのショートカット メニューを開きを選択し、**開く**でファイルを表示する、 **XML エディター**です。  
  
9. Sdkmanifest.xml 内のファイルに次のコードを追加します。  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <FileList  
      DisplayName="Simple Math"  
      MinVSVersion="14.0"  
      AppliesTo="JavaScript+WindowsAppContainer"  
      SupportsMultipleVersions="Error"  
      MoreInfo="http://www.msdn.microsoft.com/">  
  
      <!-- JS -->  
      <File Content="js\arithmetic.js" />  
    </FileList>  
  
    ```  
  
10. **ソリューション エクスプ ローラー**、sdkmanifest.xml 内のファイルのショートカット メニューで**プロパティ**です。  
  
11. **プロパティ**ウィンドウで、設定、 **VSIX に含める**プロパティを**True**です。  
  
12. **ソリューション エクスプ ローラー**、SimpleMathVSIX プロジェクトのショートカット メニューで**追加**、**新しいフォルダー**をクリックし、フォルダーを名`Redist`です。  
  
13. このフォルダー構造を作成する再頒布可能パッケージの下にあるサブフォルダーを追加します。  
  
     \Redist\CommonConfiguration\Neutral\SimpleMath\js\  
  
14. \Js\ フォルダーのショートカット メニューで**追加**、**新しい項目の**します。  
  
15. **Visual c# アイテム**を選択、 **Web**カテゴリをクリックし、 **JavaScript ファイル**項目。 ファイルの名前を付けます`arithmetic.js`を選択し、**追加**ボタンをクリックします。  
  
16. Arithmetic.js に次のコードを挿入します。  
  
    ```  
    (function (global) {  
        "use strict";  
        global.Arithmetic = {  
            add: function (firstNumber, secondNumber) {  
                return firstNumber + secondNumber;  
            },  
  
            subtract: function (firstNumber, secondNumber) {  
                return firstNumber - secondNumber;  
            },  
  
            multiply: function (firstNumber, secondNumber) {  
                return firstNumber * secondNumber;  
            },  
  
            divide: function (firstNumber, secondNumber) {  
                return firstNumber / secondNumber;  
            }  
        };  
    })(this);  
  
    ```  
  
17. **ソリューション エクスプ ローラー**、arithmetic.js ファイルのショートカット メニューで**プロパティ**です。 これらのプロパティの変更を行います。  
  
    -   設定、 **VSIX に含める**プロパティを**True**です。  
  
    -   設定、**出力ディレクトリにコピー**プロパティを**常にコピー**です。  
  
18. **ソリューション エクスプ ローラー**、SimpleMathVSIX プロジェクトのショートカット メニューで**ビルド**です。  
  
19. ビルドが完了したら、プロジェクトのショートカット メニューを選択**ファイル エクスプ ローラーでフォルダーを開く**です。 \Bin\debug に移動\\、および実行`SimpleMathVSIX.vsix`をインストールします。  
  
20. 選択、**インストール**ボタンをクリックし、インストールを完了します。  
  
21. Visual Studio を再起動します。  
  
##  <a name="createSampleApp"></a> SDK を使用するサンプル アプリを作成するには  
  
1.  メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]**の順にクリックします。  
  
2.  テンプレート カテゴリの一覧で  **JavaScript** **Windows ストア**、し、、**空のアプリケーション**テンプレート。  
  
3.  **名前**ボックスで、指定`ArithmeticUI`です。 **[OK]** を選択します。  
  
4.  **ソリューション エクスプ ローラー**ArithmeticUI プロジェクトのショートカット メニューを開きを選択し、**追加**、**参照**です。  
  
5.  **Windows**を選択**拡張**、ことを確認**単純な計算**が表示されます。  
  
6.  選択、**単純な計算**チェック ボックスをオンにして、 **OK**ボタンをクリックします。  
  
7.  **ソリューション エクスプ ローラー****参照**、ことに注意して、**単純な計算**参照が表示されます。 展開し、arithmetic.js を含む \js\ フォルダーがあることに注意してください。 ソース コードがインストールされていることを確認する arithmetic.js を開くことができます。  
  
8.  Default.htm の内容を置き換えるには、次のコードを使用します。  
  
    ```  
    <!DOCTYPE html>  
    <html>  
    <head>  
        <meta charset="utf-8" />  
        <title>ArithmeticUI</title>  
  
        <!-- WinJS references -->  
        <link href="//Microsoft.WinJS.1.0/css/ui-dark.css" rel="stylesheet" />  
        <script src="//Microsoft.WinJS.1.0/js/base.js"></script>  
        <script src="//Microsoft.WinJS.1.0/js/ui.js"></script>  
  
        <!-- ArithmeticUI references -->  
        <link href="/css/default.css" rel="stylesheet" />  
        <script src="/js/default.js"></script>  
        <script src="/SimpleMath/js/arithmetic.js"></script>  
    </head>  
    <body>  
        <form>  
        <div id="calculator" class="ms-grid">  
            <input name="firstNumber" id="firstNumber" type="number" step="any">  
            <div id="operators">  
                <button class="operator" type="button">+</button>  
                <button class="operator" type="button">-</button>  
                <button class="operator" type="button">*</button>  
                <button class="operator" type="button">/</button>  
            </div>  
            <input id="secondNumber" type="number">  
            <button class="calculate" type="button">=</button>  
            <input id="result" type="number" name="result" disabled="" readonly="">  
        </div>  
        </form>  
    </body>  
    </html>  
    ```  
  
9. 次のコードを使用して、\js\default.js の内容に置き換えます。  
  
    ```  
    (function () {  
        "use strict";  
  
        var app = WinJS.Application;  
        var operation = null;  
  
        function calculateResult() {  
            var firstNumber = parseFloat(document.querySelector("#firstNumber").value),  
                secondNumber = parseFloat(document.querySelector("#secondNumber").value),  
                result = 0;  
  
            if (isNaN(firstNumber) || isNaN(secondNumber)) {  
                result = 0;  
            }  
            else {  
                switch (operation) {  
                    case "+":  
                        result = Arithmetic.add(firstNumber, secondNumber);  
                        break;  
                    case "-":  
                        result = Arithmetic.subtract(firstNumber, secondNumber);  
                        break;  
                    case "*":  
                        result = Arithmetic.multiply(firstNumber, secondNumber);  
                        break;  
                    case "/":  
                        result = Arithmetic.divide(firstNumber, secondNumber);  
                        break;  
                    default:  
                }  
            }  
            document.querySelector("#result").value = result.toString();  
        }  
  
        app.onactivated = function (args) {  
            document.querySelector("#calculator").addEventListener("click", function (event) {  
                if (event.target.tagName.toLowerCase() === "button") {  
                    switch (event.target.className) {  
                        case "operator":  
                            operation = event.target.innerText;  
                            break;  
                        case "calculate":  
                            calculateResult();  
                            break;  
                        default:  
                            break;  
                    }  
                }  
            });  
        };  
  
        app.start();  
    })();  
    ```  
  
10. このコードで \css\default.css の内容を置き換えます。  
  
    ```  
    form {  
        display: -ms-grid;  
        -ms-grid-rows: 1fr auto 1fr;  
        -ms-grid-columns: 1fr auto 1fr;  
        height: 100%;  
        width: 100%;  
    }  
  
    button, input[type=number] {  
        margin-right: 5px;  
        -ms-grid-row-align: center;  
    }  
  
    #calculator {  
        -ms-grid-column: 2;  
        -ms-grid-row: 2;  
        display: -ms-grid;  
        -ms-grid-rows: 1fr;  
        -ms-grid-columns: auto min-content auto auto auto;  
    }  
  
    .ms-grid input {  
        width: 5em;  
    }  
  
    #firstNumber {  
        -ms-grid-column: 1;  
        -ms-grid-row-align: center;  
    }  
  
    #operators {  
        -ms-grid-column: 2;  
        -ms-grid-row-align: center;  
    }  
  
        #operators button.operator {  
            margin-bottom: 5px;  
            height: 40px;  
        }  
  
    #secondNumber {  
        -ms-grid-column: 3;  
    }  
  
    button.calculate {  
        -ms-grid-column: 4;  
        -ms-grid-row-align: center;  
        height: 40px;  
    }  
  
    #result {  
        -ms-grid-column: 5;  
    }  
  
    ```  
  
11. F5 キーをアプリをビルドして実行を選択します。  
  
12. UI のアプリで、2 つの数値を入力してください。、、の操作を選択し、、 **=**ボタンをクリックします。 正しい結果が表示されます。  
  
## <a name="see-also"></a>関連項目  
 [ソフトウェア開発キットを作成する](../extensibility/creating-a-software-development-kit.md)