---
description: Hosten von Webinhalten in Ihrer WPF-App mit dem Steuerelement "Microsoft Edge WebView 2"
title: Microsoft Edge WebView 2 für WPF-apps
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 05/12/2020
ms.topic: conceptual
ms.prod: microsoft-edge
ms.technology: webview
keywords: WebView2, WebView2, WebView, WebView, WPF-apps, WPF, Edge, CoreWebView2, Browser-Steuerelement, Edge-HTML, erste Schritte, erste Schritte, .net
ms.openlocfilehash: ebff559a940c54dcea18dec58170bdee1e030e9b
ms.sourcegitcommit: 799fe63d961a37ada455bb36ef3ef0d8076e70bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2020
ms.locfileid: "10685694"
---
# Erste Schritte mit WebView2 in WPF (Preview)  

In diesem Artikel erfahren Sie, wie Sie Ihre erste WebView2-app erstellen und die wichtigsten Features von [WebView2 (Preview)](/microsoft-edge/hosting/webview2/index)kennenlernen.  Weitere Informationen zu einzelnen APIs finden Sie unter [API-Referenz](../reference/dotnet/0-9-515-reference-webview2.md).  

## Voraussetzungen  

Stellen Sie sicher, dass Sie die folgende Liste der Voraussetzungen installiert haben, bevor Sie fortfahren:  

* [Microsoft Edge (Chrom) Canary Channel](https://www.microsoftedgeinsider.com/download/) , installiert unter Windows 10, Windows 8,1 oder Windows 7. 
* [Visual Studio](https://visualstudio.microsoft.com/) 2017 oder höher  

## Schritt 1 – Erstellen einer einzelnen Fenster Anwendung

Beginnen Sie mit einem einfachen Desktopprojekt, das ein einzelnes Hauptfenster enthält.  

1. Öffnen Sie **Visual Studio.**
2. Wählen Sie **WPF .net Core-App** oder **WPF .NET Framework-App**aus, und wählen Sie dann **weiter**aus.  

    :::row:::
       :::column span="1":::
          :::image type="complex" source="./media/wpf-gettingstarted-wpfcore.png" alt-text="WPF-Kern":::
             WPF-Kern :::image-end:::
       :::column-end:::
       :::column span="1":::
          :::image type="complex" source="./media/wpf-gettingstarted-wpffw.png" alt-text="WPF-Framework":::
             WPF-Framework :::image-end:::
       :::column-end:::
    :::row-end:::

3. Geben Sie Werte für **Projektname** und **Speicherort**ein.  Wählen Sie .NET Framework 4.6.2 oder höher oder .net Core 3,0 oder höher aus.  

:::row:::
       :::column span="1":::
          :::image type="complex" source="./media/wpf-gettingstarted-createcore.png" alt-text="Erstellen eines Kerns":::
             Erstellen eines Kerns :::image-end:::
       :::column-end:::
       :::column span="1":::
          :::image type="complex" source="./media/wpf-gettingstarted-createfw.png" alt-text="Erstellen eines Frameworks":::
             Erstellen eines Frameworks :::image-end:::
       :::column-end:::
    :::row-end:::

4. Wählen Sie **Erstellen** aus, um Ihr Projekt zu erstellen.  

## Schritt 2 – Installieren des WebView2 SDK  

Fügen Sie als nächstes das WebView2-SDK zum Projekt hinzu.  Installieren Sie für die Vorschau das WebView2-SDK mithilfe von Nuget.  

1. Öffnen Sie das Kontextmenü im Projekt \ (Klicken Sie mit der rechten Maustaste auf \), und wählen Sie **NuGet-Pakete verwalten**aus.  

    :::image type="complex" source="./media/wpf-gettingstarted-mngnuget.png" alt-text="Nuget":::
       Nuget :::image-end:::

2. Geben Sie `Microsoft.Web.WebView2` in die Suchleiste ein.  Wählen Sie in den Suchergebnissen **Microsoft. Web. WebView2** aus.  Legen Sie die Paketversion auf **Pre-Release**, und wählen Sie dann **Installieren**aus.  

     ![nuget](./media/installnuget.PNG)

Sie können mit der WebView2-API beginnen, Anwendungen zu entwickeln.  Drücken Sie `F5` , um das Projekt zu erstellen und auszuführen.  Im laufenden Projekt wird ein leeres Fenster angezeigt.  

:::image type="complex" source="./media/wpf-gettingstarted-blank.png" alt-text="Leere App":::
   Leere App
:::image-end:::

## Schritt 3 – Erstellen einer einzelnen WebView in "" "" ". XAML"  

Fügen Sie Ihrer Anwendung als nächstes eine WebView hinzu.  

1. Öffnen Sie `MainWindow.xaml`.  Fügen Sie den WebView2-XAML-Namespace hinzu, indem Sie die folgende Zeile innerhalb der `<Window/>` Kategorie einfügen.  

    ```xml
    xmlns:wv2="clr-namespace:Microsoft.Web.WebView2.Wpf;assembly=Microsoft.Web.WebView2.Wpf"
    ```  

    Vergewissern Sie sich, dass der Code in `MainWindow.xaml` wie im folgenden Codeausschnitt aussieht.  

    ```xml
    <Window x:Class="WPF_Getting_Started.MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
            xmlns:local="clr-namespace:{YOUR PROJECT NAME}"
            xmlns:wv2="clr-namespace:Microsoft.Web.WebView2.Wpf;assembly=Microsoft.Web.WebView2.Wpf"
            mc:Ignorable="d"
            Title="MainWindow"
            Height="450"
            Width="800"
        />
        <Grid>

                </Grid>
    </Window>
    ```  

2. Fügen Sie das WebView2-Steuerelement hinzu, indem Sie die `<Grid>` Tags mit dem folgenden Codeausschnitt ersetzen.  Die `Source` Eigenschaft legt den anfänglichen URI fest, der im WebView2-Steuerelement angezeigt wird.  

    ```xml  
    <DockPanel>
        <wv2:WebView2 Name="webView"
                      Source="https://www.microsoft.com"
        />
    </DockPanel>
    ```  

3. Drücken Sie `F5` , um das Projekt zu erstellen und auszuführen.  Vergewissern Sie sich, dass Ihr WebView2-Steuerelement angezeigt wird [https://www.microsoft.com](https://www.microsoft.com) .  

    :::image type="complex" source="./media/wpf-gettingstarted-microsoft.png" alt-text="Microsoft.com":::
       Microsoft.com :::image-end:::

## Schritt 4 – Navigation  

Hinzufügen der Möglichkeit, dass Benutzer die vom WebView2-Steuerelement angezeigte URL ändern können, indem Sie der App eine Adressleiste hinzufügen.

1. Fügen Sie in "Hauptfeld **. XAML**" eine Adressleiste hinzu, indem Sie den folgenden Codeausschnitt innerhalb der DockPanel-Datei, die die WebView enthält, kopieren und einfügen.  

```xml
<DockPanel DockPanel.Dock="Top">
    <Button x:Name="ButtonGo"
            DockPanel.Dock="Right"
            Click="ButtonGo_Click"
            Content="Go"
    />
    <TextBox Name="addressBar"/>
</DockPanel>
```  

Vergewissern Sie sich, dass der `DockPanel` Abschnitt `MainWindow.xaml` wie im folgenden Codeausschnitt aussieht.  

```xml
<DockPanel>
    <DockPanel DockPanel.Dock="Top">
        <Button x:Name="ButtonGo" DockPanel.Dock="Right" Click="ButtonGo_Click" Content="Go"/>
        <TextBox Name = "addressBar"/>
    </DockPanel>
    <wv2:WebView2 Name = "webView"
                  Source = "https://www.microsoft.com"
    />
</DockPanel>
```  

2. `MainWindow.xaml.cs`In Visual Studio öffnen.  Fügen Sie den `CoreWebView2` Namespace hinzu, indem Sie am oberen Rand des folgenden Codeausschnitts einfügen `MainWindow.xaml.cs` .  

    ```csharp
    using Microsoft.Web.WebView2.Core;
    ```

3. Kopieren Sie in **MainWindow.XAML.cs**den folgenden Codeausschnitt, um die `ButtonGo_Click` Methode zu erstellen, die die WebView zu der in der Adressleiste eingegebenen URL navigiert.  

    ```csharp
    private void ButtonGo_Click(object sender, RoutedEventArgs e)
    {
        if (webView != null && webView.CoreWebView2 != null)
        {
            webView.CoreWebView2.Navigate(addressBar.Text);
        }
    }
    ```  

Drücken Sie `F5` , um das Projekt zu erstellen und auszuführen.  Geben Sie in der Adressleiste eine neue URL ein, und klicken Sie auf **Gehe**zu.  Geben Sie beispielsweise ein `https://www.bing.com` .  Überprüfen Sie, ob das WebView2-Steuerelement zur URL navigiert.  

> [!NOTE]
> Stellen Sie sicher, dass in der Adressleiste eine vollständige URL eingegeben wurde. Eine `ArgumentException` wird ausgelöst, wenn die URL nicht mit gestartet wird `http://` oder `https://`

:::image type="complex" source="./media/wpf-gettingstarted-bing.png" alt-text="Bing":::
   Bing
:::image-end:::

## Schritt 5 – Navigationsereignisse  

Die Anwendung, die WebView2-Steuerelemente hostet, überwacht die folgenden Ereignisse, die vom WebView2-Steuerelement während der Navigation zu Webseiten ausgelöst werden.  

* `NavigationStarting`  
* `SourceChanged`  
* `ContentLoading`  
* `HistoryChanged`  
* `NavigationCompleted`  

Weitere Informationen finden Sie unter [Navigationsereignisse](../reference/win32/0-9-488/icorewebview2.md#navigation-events).  

:::image type="complex" source="../media/navigation-events.png" alt-text="Navigationsereignisse":::
   Navigationsereignisse
:::image-end:::

Wenn ein Fehler auftritt, werden die folgenden Ereignisse ausgelöst und können von der Navigation zu einer Fehlerseite abhängen.  

* `SourceChanged`  
* `ContentLoading`  
* `HistoryChanged`  

Wenn eine HTTP-Umleitung vorhanden ist, gibt es mehrere `NavigationStarting` Ereignisse.  

Um zu veranschaulichen, wie diese Ereignisse verwendet werden, müssen Sie zunächst einen Handler registrieren, der `NavigationStarting` alle Anforderungen abbricht, die nicht HTTPS verwenden.  

`MainWindow.xaml.cs`Ändern Sie in den Konstruktor wie unten dargestellt, und fügen Sie die `EnsureHttps` Funktion hinzu.  

```csharp
public MainWindow()
{
    InitializeComponent();
    webView.NavigationStarting += EnsureHttps;
}

void EnsureHttps(object sender, CoreWebView2NavigationStartingEventArgs args)
{
    String uri = args.Uri;
    if (!uri.StartsWith("https://"))
    {
        args.Cancel = true;
    }
}
```

Im Konstruktor wird EnsureHttps als Ereignishandler für das `NavigationStarting` Ereignis im WebView2-Steuerelement registriert.  

Drücken Sie `F5` , um das Projekt zu erstellen und auszuführen. Vergewissern Sie sich, dass die WebView-Ansicht beim Navigieren zu einer HTTP-Website **unverändert bleibt**. Die WebView wird jedoch zu HTTPS-Websites navigieren.

## Schritt 6 – Skripting  

Sie können Host-Anwendungen verwenden, um JavaScript-Code zur Laufzeit in WebView2-Steuerelemente einzufügen.  Das eingefügte JavaScript gilt für alle neuen Dokumente auf oberster Ebene und für alle untergeordneten Frames, bis das JavaScript entfernt wurde.  Das eingefügte JavaScript wird nach der Erstellung des globalen Objekts und vor dem Ausführen eines anderen im HTML-Dokument enthaltenen Skripts ausgeführt.  

Sie können Skripting verwenden, um den Benutzer zu benachrichtigen, wenn Sie zu einer nicht-HTTPS-Website navigieren.  Ändern `EnsureHttps` Sie die Funktion so, dass Sie mit der [ExecuteScriptAsync](../reference/wpf/0-9-515/microsoft-web-webview2-wpf-webview2.md#executescriptasync) -Methode Skripts in den Webinhalt einfügt.  

```csharp
void EnsureHttps(object sender, CoreWebView2NavigationStartingEventArgs args)
{
    String uri = args.Uri;
    if (!uri.StartsWith("https://"))
    {
        webView.CoreWebView2.ExecuteScriptAsync($"alert('{uri} is not safe, try an https link')");
        args.Cancel = true;
    }
}
```  

Drücken Sie `F5` , um das Projekt zu erstellen und auszuführen.  Vergewissern Sie sich, dass die Anwendung eine Warnung anzeigt, wenn Sie zu einer Website navigieren, die nicht HTTPS verwendet.  

:::image type="complex" source="./media/wpf-gettingstarted-https.png" alt-text="HTTPS":::
   HTTPS
:::image-end:::

## Schritt 7 – Kommunikation zwischen Host-und Webinhalten  

Die Host-und Webinhalte können mithilfe der folgenden Informationen miteinander kommunizieren `postMessage` :  

* Webinhalte in einem WebView2-Steuerelement senden möglicherweise eine Nachricht mithilfe von an den Host `window.chrome.webview.postMessage` .  Der Host verarbeitet die Nachricht mit einem `WebMessageReceived` auf dem Host registrierten Namen.  
* Hosts Posten Nachrichten an Webinhalte in einem WebView2-Steuerelement mit `CoreWebView2.PostWebMessageAsString` oder `CoreWebView2.PostWebMessageAsJSON` .  Diese Nachrichten werden von Handlern abgefangen, denen Sie hinzugefügt wurden `window.chrome.webview.addEventListener` .  

Mit diesem Kommunikationsmechanismus können Webinhalte Nachrichten mithilfe von systemeigenen Funktionen an den Host weiterleiten.  

Wenn das WebView2-Steuerelement in Ihrem Projekt zu einer URL navigiert, wird die URL in der Adressleiste angezeigt, und der Benutzer wird benachrichtigt, dass die URL im WebView2-Steuerelement angezeigt wird.  

1. Aktualisieren Sie in **MainWindow.XAML.cs**den Konstruktor, und erstellen Sie eine `InitializeAsync` Funktion, wie im folgenden Codeausschnitt dargestellt.  Die `InitializeAsync` Funktion wartet [EnsureCoreWebView2Async](../reference/wpf/0-9-515/microsoft-web-webview2-wpf-webview2.md#ensurecorewebview2async) auf, da die Initialisierung von `CoreWebView2` asynchron ist.  

    ```csharp
    public MainWindow()
    {
        InitializeComponent();
        webView.NavigationStarting += EnsureHttps;
        InitializeAsync();
    }

    async void InitializeAsync()
    {
        await webView.EnsureCoreWebView2Async(null);
    }
    ```  

2. Nachdem **CoreWebView2** initialisiert wurde, registrieren Sie einen Ereignishandler, auf den Sie Antworten können `WebMessageReceived` .  In **MainWindow.XAML.cs** Update `InitializeAsync` und Add `UpdateAddressBar` mit dem folgenden Codeausschnitt.  

    ```csharp
    async void InitializeAsync()
    {
        await webView.EnsureCoreWebView2Async(null);
        webView.CoreWebView2.WebMessageReceived += UpdateAddressBar;
    }

    void UpdateAddressBar(object sender, CoreWebView2WebMessageReceivedEventArgs args)
    {
        String uri = args.TryGetWebMessageAsString();
        addressBar.Text = uri;
        webView.CoreWebView2.PostWebMessageAsString(uri);
    }
    ```  

3. Damit die WebView die Webnachricht senden und beantworten kann, `CoreWebView2` wird nach der Initialisierung der Host:  

    1. Fügt dem Webinhalt ein Skript ein, das einen Handler registriert, um eine Nachricht vom Host zu drucken.  
    2. Fügt dem Webinhalt ein Skript hinzu, das die URL an den Host sendet.  

In `MainWindow.xaml.cs` , aktualisieren Sie `InitializeAsync` wie folgt:  

```csharp
async void InitializeAsync()
{
    await webView.EnsureCoreWebView2Async(null);
    webView.CoreWebView2.WebMessageReceived += UpdateAddressBar;

    await webView.CoreWebView2.AddScriptToExecuteOnDocumentCreatedAsync("window.chrome.webview.postMessage(window.document.URL);");
    await webView.CoreWebView2.AddScriptToExecuteOnDocumentCreatedAsync("window.chrome.webview.addEventListener(\'message\', event => alert(event.data));");
}
```  

Drücken Sie `F5` , um die APP zu erstellen und auszuführen.  Die Adressleiste zeigt nun den URI in der WebView an, und wenn Sie erfolgreich zu einem neuen URI navigieren, benachrichtigt die WebView den Benutzer des in der WebView angezeigten URIs.  

:::image type="complex" source="./media/wpf-gettingstarted-searchbar.png" alt-text="addressBar":::
   addressBar
:::image-end:::

Herzlichen Glückwunsch, Sie haben ihre erste WebView2-App erstellt!  

## Nächste Schritte  

* Auschecken des [WebView2Samples Repo](https://github.com/MicrosoftEdge/WebView2Samples) für ein umfassendes Beispiel für WebView2's-Funktionen
* Checkout [-API-Referenz](../reference/wpf/0-9-515/microsoft-web-webview2-wpf-webview2) für detailliertere Informationen zu unseren APIs
* Auschecken einer Liste mit [WebView2-Ressourcen](../index.md#next-steps) , um mehr über WebView2 zu erfahren

## Kontakt mit dem Microsoft Edge WebView-Team  

Helfen Sie, ein reicheres WebView2-Erlebnis zu schaffen, indem Sie Ihr Feedback austauschen!  Besuchen Sie das Feedback- [Repo](https://aka.ms/webviewfeedback) von Microsoft Edge WebView, um Funktionsanforderungen oder Fehlerberichte zu übermitteln oder nach bekannten Problemen zu suchen.  
