---
layout: default
title: Materialsammlung
---

<table id="materialTable">
  <thead>
    <tr>
      <th class="sortable" data-column="thema">Quelle</th>
      <th class="sortable" data-column="fach">Fach</th>
      <th class="sortable" data-column="klasse">Klasse</th>
      <th class="sortable" data-column="bereich">Bereich</th>
      <th>Beschreibung / Hinweis</th>
    </tr>
  </thead>
  <tbody id="tableBody">
    {% for source in site.sources %}
      <tr data-id="{{ source.sid }}">
        <td>
          <div class="source-link">
          {% if source.source_link == nil or source.source_link == "" %}
            <a href="{{ site.yt_base }}/embed/{{ source.youtube_id }}{%- if source.youtube_time_start or source.youtube_time_end -%}?
                {%- if source.youtube_time_start -%}t={{ source.youtube_time_start }}{%- endif -%}
                {%- if source.youtube_time_start and source.youtube_time_end -%}&{%- endif -%}
                {%- if source.youtube_time_end -%}end={{ source.youtube_time_end }}{%- endif -%}
            {% endif %}">
                <strong>{{ source.thema }}</strong>
            </a>
          {% else %}
            <a href="{{ source.source_link }}"><strong>{{ source.thema }}</strong></a>
          {% endif %}
          </div>
          <a href="/?id={{ source.sid }}" title="share" onclick="navigator.clipboard.writeText(window.location.protocol + '//' + window.location.hostname + (window.location.port ? ':' + window.location.port : '') + this.getAttribute('href'))">
          <i class="fas fa-share-nodes"></i>
          </a>
          {% if source.source_link == nil or source.source_link == "" %}
          <a href="javascript:void(0)" title="copy link" onclick="copyIframeToClipboard('{{ source.sid }}')">
            <i class="fas fa-circle-play"></i>
          </a>
          {% endif %}
          <i class="fas fa-info-circle info-icon" data-reviewed-from="{{ source.reviewed_from }}" data-reviewed-on="{{ source.reviewed_on }}"></i>
        </td>
        <td>{{ source.fach }}</td>
        <td>Klassenstufe {{ source.klasse }}</td>
        <td>{{ source.bereich }}</td>
        <td>{{ source.beschreibung }}</td>
      </tr>
    {% endfor %}
  </tbody>
</table>