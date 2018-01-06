---
title: "チュートリアル: エディターの拡張機能とショートカット キーを使用する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
caps.latest.revision: "32"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 60cfb35e2c3acbe3b52f460b040dd5c220e6b045
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-using-a-shortcut-key-with-an-editor-extension"></a>チュートリアル: エディターの拡張機能とショートカット キーを使用します。
エディター拡張機能で、ショートカット キーに応答することができます。 次のチュートリアルでは、テキスト ビューにショートカット キーを使用してビューの表示要素を追加する方法を示します。 このチュートリアルは、ビューポート装飾エディター テンプレートに基づいておりを使用して表示要素を追加することができます、プラス記号です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降で、ダウンロード センターから、Visual Studio SDK をインストールするはできません。 Visual Studio のセットアップのオプション機能として含まれます。 後でまた VS SDK をインストールすることができます。 詳細については、次を参照してください。 [、Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) プロジェクトの作成  
  
1.  C# の場合は、VSIX プロジェクトを作成します。 (で、**新しいプロジェクト**ダイアログで、 **Visual c#/機能拡張**、し**VSIX プロジェクト**)。ソリューションの名前を付けます`KeyBindingTest`です。  
  
2.  エディターのテキスト装飾項目テンプレートをプロジェクトに追加し、名前を付けます`KeyBindingTest`です。 詳細については、次を参照してください。[エディター項目テンプレートに、拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)です。  
  
3.  次の参照を追加し、設定**CopyLocal**に`false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
 KeyBindingTest クラス ファイルでは、PurpleCornerBox にクラス名を変更します。 左側の余白に電球が表示されますを使用して、その他の適切な変更を行います。 コンス トラクター内からレイヤーを表示要素の名前を変更する**KeyBindingTest**に**PurpleCornerBox**:  
  
```csharp  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  
  
## <a name="defining-the-command-filter"></a>コマンドのフィルターを定義します。  
 コマンドのフィルターの実装は、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>、表示要素をインスタンス化して、コマンドを処理します。  
  
1.  クラス ファイルを追加し、名前を付けます`KeyBindingCommandFilter`です。  
  
2.  次の using ステートメントを追加します。  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3.  KeyBindingCommandFilter をという名前のクラスを継承する必要があります<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>です。  
  
    ```csharp  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4.  コマンドのチェーン、およびコマンド フィルターは既に追加されているかどうかを表すフラグでテキスト ビューのプライベート フィールドを次のコマンドを追加します。  
  
    ```csharp  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
    ```  
  
5.  テキスト ビューを設定するコンス トラクターを追加します。  
  
    ```csharp  
    public KeyBindingCommandFilter(IWpfTextView textView)  
    {  
        m_textView = textView;  
        m_adorned = false;  
    }  
    ```  
  
6.  実装、`QueryStatus()`メソッドを次のようにします。  
  
    ```vb  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7.  実装、`Exec()`場合をビューに紫色のボックスを追加するためのメソッド、文字が入力されたとします。  
  
    ```csharp  
    int IOleCommandTarget.Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
    {  
        if (m_adorned == false)  
        {  
            char typedChar = char.MinValue;  
  
            if (pguidCmdGroup == VSConstants.VSStd2K && nCmdID == (uint)VSConstants.VSStd2KCmdID.TYPECHAR)  
            {  
                typedChar = (char)(ushort)Marshal.GetObjectForNativeVariant(pvaIn);  
                if (typedChar.Equals('+'))  
                {  
                    new PurpleCornerBox(m_textView);  
                    m_adorned = true;  
                }  
            }  
        }  
        return m_nextTarget.Exec(ref pguidCmdGroup, nCmdID, nCmdexecopt, pvaIn, pvaOut);  
    }  
  
    ```  
  
## <a name="adding-the-command-filter"></a>コマンドのフィルターを追加します。  
 装飾プロバイダーは、テキスト ビューにコマンドのフィルターを追加する必要があります。 この例では、プロバイダーを実装する<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>テキスト ビューの作成イベントをリッスンするようにします。 この表示要素のプロバイダーでは、表示要素の Z オーダーを定義する装飾層をエクスポートします。  
  
1.  次のコードを追加、KeyBindingTestTextViewCreationListener ファイルでステートメントを使用します。  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.Utilities;  
    using Microsoft.VisualStudio.Editor;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.TextManager.Interop;  
  
    ```  
  
2.  装飾層の定義でから AdornmentLayer の名前変更**KeyBindingTest**に**PurpleCornerBox**です。  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3.  テキスト ビュー アダプターを取得するには、インポートする必要があります、<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>です。  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
4.  変更、<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>メソッドが追加されますので、`KeyBindingCommandFilter`です。  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
5.  `AddCommandFilter`ハンドラーは、テキスト ビュー アダプターを取得し、コマンドのフィルターを追加します。  
  
    ```csharp  
    void AddCommandFilter(IWpfTextView textView, KeyBindingCommandFilter commandFilter)  
    {  
        if (commandFilter.m_added == false)  
        {  
            //get the view adapter from the editor factory  
            IOleCommandTarget next;   
            IVsTextView view = editorFactory.GetViewAdapter(textView);  
  
            int hr = view.AddCommandFilter(commandFilter, out next);  
  
            if (hr == VSConstants.S_OK)  
            {      
                commandFilter.m_added = true;  
                 //you'll need the next target for Exec and QueryStatus   
                if (next != null)  
                commandFilter.m_nextTarget = next;  
            }  
        }  
    }  
    ```  
  
## <a name="making-the-adornment-appear-on-every-line"></a>表示要素を行うすべての行に表示されます  
 すべての文字で表示されていた元の表示要素の ' a' をテキスト ファイルにします。 行にのみ表示要素を追加するので、'+' の文字への応答の表示要素を追加するコードを変更しましたが、ここで、'+' は型指定されています。 1 回以上表示要素が表示されるように、装飾コードを変更できますすべて 'a' です。  
  
 KeyBindingTest.cs ファイルでは、'a' 文字の装飾にビューのすべての行を反復処理する CreateVisuals() メソッドを変更します。  
  
```csharp  
private void CreateVisuals(ITextViewLine line)  
{  
    IWpfTextViewLineCollection textViewLines = this.view.TextViewLines;  
  
    foreach (ITextViewLine textViewLine in textViewLines)  
    {  
        if (textViewLine.ToString().Contains("a"))  
        {  
            // Loop through each character, and place a box around any 'a'   
            for (int charIndex = textViewLine.Start; charIndex < textViewLine.End; charIndex++)  
            {  
                if (this.view.TextSnapshot[charIndex] == 'a')  
                {  
                    SnapshotSpan span = new SnapshotSpan(this.view.TextSnapshot, Span.FromBounds(charIndex, charIndex + 1));  
                    Geometry geometry = textViewLines.GetMarkerGeometry(span);  
                    if (geometry != null)  
                    {  
                        var drawing = new GeometryDrawing(this.brush, this.pen, geometry);  
                        drawing.Freeze();  
  
                        var drawingImage = new DrawingImage(drawing);  
                        drawingImage.Freeze();  
  
                        var image = new Image  
                        {  
                            Source = drawingImage,  
                        };  
  
                        // Align the image with the top of the bounds of the text geometry  
                        Canvas.SetLeft(image, geometry.Bounds.Left);  
                        Canvas.SetTop(image, geometry.Bounds.Top);  
  
                        this.layer.AddAdornment(AdornmentPositioningBehavior.TextRelative, span, null, image, null);  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="building-and-testing-the-code"></a>コードのビルドとテスト  
  
1.  KeyBindingTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
2.  作成またはテキスト ファイルを開きます。 文字を含む一部の単語の入力 '、' し、入力 + テキスト ビューで任意の場所。  
  
     紫色の四角形は、ファイルの 'a' すべての文字に表示されます。